package pkg;

import java.awt.BorderLayout;

import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.JTextField;

public class TestCalculater extends JFrame {

	TestCalculater() {
		
		setTitle("계산기");
		setLayout(new BorderLayout(10,10));
		
		showNorth();
		
		
		setSize(320,670);
		setDefaultCloseOperation(EXIT_ON_CLOSE);
		this.setIconImage(getIconImage());
		setVisible(true);
		
	}
	
	void showNorth() {
		
		JTextField t = new JTextField("0",100);
	
		add(t, BorderLayout.NORTH);
		
		
	}
	
	
	
	public static void main(String[] args) {
		new TestCalculater();
	}

}
