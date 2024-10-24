package pkg;

import java.awt.BorderLayout;
import java.awt.CardLayout;
import java.awt.Color;
import java.awt.FlowLayout;
import java.awt.GridLayout;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.JTextField;

public class TestCalculater extends JFrame {

    JTextField t,t1,t2,t3;
    JPanel p;
    int mix = 0;
    double b;

    TestCalculater() {
        setTitle("계산기");
        setLayout(new BorderLayout(10, 10));

        showNorth();
        showCenter();

        setSize(320, 670);
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        this.setIconImage(getIconImage());
        setVisible(true);
    }

    void showNorth() {
  
        JPanel p1 = new JPanel(new CardLayout()); //카드레이아웃으로 3가지의 필드를 통해 사용
        
        
        t1 = new JTextField("0", 27);
        t1.setHorizontalAlignment(JTextField.RIGHT);
        t1.setSize(100, 100);
        p1.add(t1);

        add(p1, BorderLayout.NORTH);
    }
    
    

    void showCenter() {
        String[][] Text = { { " ", " ", " ", "X" }, { "7", "8", "9", "x" }, { "4", "5", "6", "-" },
                { "1", "2", "3", "+" }, { " ", "0", ".", "=" } };

        p = new JPanel(new GridLayout(5, 5, 2, 2));

        for (int i = 0; i < Text.length; i++) {
            for (int j = 0; j < Text[i].length; j++) {
                JButton bt = new JButton(Text[i][j]);
                bt.setBackground(Color.WHITE);
                
     
                bt.setActionCommand(Text[i][j]);

                bt.addActionListener(e -> {
                    String c = e.getActionCommand(); //여기서 버튼값을 받아서 스트링 c에 넣어줌
                    String currentText = t1.getText(); // 텍스트 필드의 텍스트 값을 가져와서 currentText에 삽입
                    
                    
                 
                    
                    
                    
                    
                    if (c.equals("X")) { //만약 스트링값이 x이면 
                        t1.setText(""); //초기화
                        t2.setText(""); //초기화
                        t3.setText(""); //초기화
                    } else if (currentText.equals("0")) { // 만약 현제 텍스트 값이 0일때 
                        t1.setText(c); //t에 다가 c의변수를 가져옴
                        t2.setText(c); //t에 다가 c의변수를 가져옴
                        t3.setText(c); //t에 다가 c의변수를 가져옴
                    } else { // c 값이 0이 아니고 x의 값이 아닐때
                        t1.setText(currentText + c); // 현제 텍스트필드 값에 c의 값을 더해줌.
                        t2.setText(currentText + c); // 현제 텍스트필드 값에 c의 값을 더해줌.
                        t3.setText(currentText + c); // 현제 텍스트필드 값에 c의 값을 더해줌.
                    }
                });

                p.add(bt);
            }
        }

        add(p, BorderLayout.CENTER);
    }

    public static void main(String[] args) {
        new TestCalculater();
    }
}
