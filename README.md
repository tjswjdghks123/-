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

	CardLayout cd;
	JPanel cardPanel, a1, a2;
	JTextField t, t1, t2, t3;
	JPanel p;
	String mix1, min2, mix3; // 더할 변수?
	double b;

	TestCalculater() {
		setTitle("계산기");
		setLayout(new BorderLayout(10, 10));

		cd = new CardLayout();
		cardPanel = new JPanel(cd);

		// 첫 번째 카드: t1 텍스트 필드를 포함하는 패널

		JPanel firstCard1 = new JPanel();
		t1 = new JTextField("0", 27);
		t1.setHorizontalAlignment(JTextField.RIGHT); // 숫자 오른쪽정렬
		firstCard1.add(t1);
		cardPanel.add(firstCard1, "Cd1");

		// 두 번째 카드: t2 텍스트 필드를 포함하는 패널
		JPanel firstCard2 = new JPanel();
		t2 = new JTextField("0", 27);
		t2.setHorizontalAlignment(JTextField.RIGHT);
		firstCard2.add(t2);
		cardPanel.add(firstCard2, "Cd2");

		// 세 번째 카드: t3 텍스트 필드를 포함하는 패널
		JPanel firstCard3 = new JPanel();
		t3 = new JTextField("0", 27);
		t3.setHorizontalAlignment(JTextField.RIGHT);
		firstCard3.add(t3);
		cardPanel.add(firstCard3, "C3");

		add(t1, BorderLayout.NORTH);

		String[][] Text = { { " ", " ", " ", "X" }, { "7", "8", "9", "x" }, { "4", "5", "6", "-" },
				{ "1", "2", "3", "+" }, { " ", "0", ".", "=" } };

		p = new JPanel(new GridLayout(5, 5, 2, 2));

		for (int i = 0; i < Text.length; i++) {
			for (int j = 0; j < Text[i].length; j++) {
				JButton bt = new JButton(Text[i][j]);
				bt.setBackground(Color.WHITE);

				bt.setActionCommand(Text[i][j]);
				bt.addActionListener(e -> {
					String c = e.getActionCommand(); // 버튼값을 받아서 스트링 c에 넣어줌
					String currentText = t1.getText(); // 텍스트 필드의 텍스트 값을 가져와서 currentText에 삽입

					// "+" 버튼 클릭 시 카드 레이아웃 전환
					if (c.equals("+")) {

						mix1 = currentText;

						cd.show(cardPanel, "card2");

						t1.setText("");
					} else if (c.equals("X")) { // 초기화 버튼
						t1.setText(""); // 초기화
					} else if (currentText.equals("0")) { // 만약 현재 텍스트가 0이라면
						t1.setText(c); // t1에 c의 값을 세팅
					} else { // 현재 텍스트가 0이 아니고 초기화 버튼이 아닐 때
						t1.setText(currentText + c); // 현재 텍스트 필드 값에 c를 추가
					}
				});

				p.add(bt);
			}
		}

		add(p, BorderLayout.CENTER);

		setSize(320, 670);
		setDefaultCloseOperation(EXIT_ON_CLOSE);
		this.setIconImage(getIconImage());
		setVisible(true);
	}

	public static void main(String[] args) {
		new TestCalculater();
	}
}
