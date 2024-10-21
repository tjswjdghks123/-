package pkg;

import java.awt.BorderLayout;
import java.awt.Color;
import java.awt.FlowLayout;
import java.awt.GridLayout;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.JTextArea;
import javax.swing.JTextField;

public class TestCalculater extends JFrame {

	TestCalculater() {
		
		setTitle("계산기");
		setLayout(new BorderLayout(10,10));
		
		showNorth();
		showCenter();
		
		setSize(320,670);
		setDefaultCloseOperation(EXIT_ON_CLOSE);
		this.setIconImage(getIconImage());
		setVisible(true);

	}

	void showNorth() {
		
		JPanel p1 = new JPanel();
		JPanel p2 = new JPanel(new FlowLayout());
		JTextField t = new JTextField("0",27);
		t.setHorizontalAlignment(JTextField.RIGHT); // 텍스트를 오른쪽으로 정렬
		t.setSize(100,100);
		p2.add(t);
		
		add(p2, BorderLayout.NORTH);
		
	}

	void showCenter() {
		
		String[][] Text = {{" "," "," ","X"},{"7","8","9","x"},{"4","5","6","-"},{"1","2","3","+"},{" ","0",".","="}};
		
		
		JPanel p = new JPanel(new GridLayout(5,5,2,2));
		
		for ( int i = 0; i < Text.length; i++ ) {
			for ( int j = 0; j < Text[i].length; j++) {
				JButton bt = new JButton();
				bt.setText(Text[i][j]);
				bt.setBackground(Color.WHITE);
				p.add(bt);
				/*
				if ( Text[i][j].equals(Text[5][5])) {
					bt.setBackground(Color.BLUE);
					bt.setForeground(Color.WHITE);
				}
				*/
			}
			
		}
		
		add(p, BorderLayout.CENTER);
		
	}

	public static void main(String[] args) {
		new TestCalculater();
	}

}
