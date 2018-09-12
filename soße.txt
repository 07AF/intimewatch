import java.awt.Font;
import java.awt.Color;
import java.awt.GridLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.Timer;
import javax.swing.SwingConstants;
import java.util.*;
import java.text.*;
 
public class DigitalClock {
 
  public static void main(String[] arguments) {
 
 
    ClockLabel timeLable = new ClockLabel("time");
  
 
    JFrame.setDefaultLookAndFeelDecorated(true);
    JFrame f = new JFrame("Uhr");
    f.setSize(600,300);
    f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
 
 
    f.add(timeLable);
 
 
    f.getContentPane().setBackground(Color.black);
 
    f.setVisible(true);
  }
}
 
class ClockLabel extends JLabel implements ActionListener {
 
  String type;
  SimpleDateFormat sdf;
 
  public ClockLabel(String type) {
    this.type = type;
    setForeground(Color.green);
 
    switch (type) {
  
      case "time" : sdf = new SimpleDateFormat("yyyyMMddHHmmss.SSS");
                    setFont(new Font("Courier New", Font.PLAIN, 100));
                    setHorizontalAlignment(SwingConstants.CENTER);
                    break;

    }
 
    Timer t = new Timer(1, this);
    t.start();
  }
 
  public void actionPerformed(ActionEvent ae) {
    Date d = new Date();
    setText(sdf.format(d));
  }
}