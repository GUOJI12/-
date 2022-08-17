package View_main;

import java.awt.BorderLayout;
import java.awt.EventQueue;

import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.border.EmptyBorder;
import javax.swing.JLabel;
import javax.swing.ImageIcon;

import java.awt.Font;

import javax.swing.JOptionPane;
import javax.swing.JTextField;
import javax.swing.JRadioButton;
import javax.swing.JButton;

import dao.AdminDao;
import dao.StudentDao;
import dao.TeacherDao;

import java.awt.event.ActionListener;
import java.awt.event.ActionEvent;

import javax.swing.JCheckBox;
import javax.swing.JPasswordField;
import javax.swing.JMenuItem;

import java.awt.Color;

import javax.swing.SwingConstants;

public class DenLu extends JFrame {

	private JPanel contentPane;
	private JTextField textField;
	private JTextField textField_1;
	JRadioButton radioButton,radioButton_1,radioButton_2;
	private JPasswordField passwordField;
	private static String id;
	
	/**
	 * Launch the application.
	 */
	public static void main(String[] args) {
		EventQueue.invokeLater(new Runnable() {
			public void run() {
				try {
					DenLu frame = new DenLu();
					frame.setVisible(true);
				} catch (Exception e) {
					e.printStackTrace();
				}
			}
		});
	}

	/**
	 * Create the frame.
	 */
	public DenLu() {
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setBounds(100, 100, 549, 484);
		contentPane = new JPanel();
		contentPane.setBorder(new EmptyBorder(5, 5, 5, 5));
		setContentPane(contentPane);
		contentPane.setLayout(null);
		
		final JLabel label = new JLabel("");
		label.setHorizontalAlignment(SwingConstants.CENTER);
		
		label.setIcon(new ImageIcon("C:\\Users\\GUOJI\\Desktop\\javas\\de1234.png"));
		label.setBounds(224, 142, 80, 94);
		contentPane.add(label);
		
		JLabel lblNewLabel_1 = new JLabel("");
		lblNewLabel_1.setIcon(new ImageIcon("C:\\Users\\GUOJI\\Desktop\\javas\\de12.png"));
		lblNewLabel_1.setBounds(0, 0, 103, 68);
		contentPane.add(lblNewLabel_1);
		
		JLabel lblNewLabel = new JLabel("");
		lblNewLabel.setIcon(new ImageIcon("C:\\Users\\GUOJI\\Desktop\\javas\\deng1.png"));
		lblNewLabel.setBounds(0, 0, 531, 197);
		contentPane.add(lblNewLabel);
		
		JLabel label_1 = new JLabel("\u8D26\u6237");
		label_1.setFont(new Font("宋体", Font.PLAIN, 20));
		label_1.setBounds(97, 247, 72, 24);
		contentPane.add(label_1);
		
		textField = new JTextField();
		textField.setBounds(160, 249, 230, 24);
		contentPane.add(textField);
		textField.setColumns(10);
		
		JLabel label_2 = new JLabel("\u5BC6\u7801");
		label_2.setFont(new Font("宋体", Font.PLAIN, 20));
		label_2.setBounds(97, 293, 72, 24);
		contentPane.add(label_2);
		
		passwordField = new JPasswordField();
		passwordField.setBounds(160, 295, 230, 24);
		contentPane.add(passwordField);
		
		textField_1 = new JTextField();
		textField_1.setColumns(10);
		textField_1.setBounds(160, 295, 230, 24);
		contentPane.add(textField_1);
		textField_1.setVisible(false);
		
		radioButton = new JRadioButton("\u5B66\u751F");
		radioButton.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent arg0) {
				if(radioButton.isSelected()){
					label.setIcon(new ImageIcon("C:\\Users\\GUOJI\\Desktop\\javas\\de1234.png"));
					StudentDao sd =new StudentDao();
					textField_1.setText(passwordField.getText());
					try {
						String tx = sd.toxiang(textField.getText(),textField_1.getText());
						if(!tx.equals("")){
						label.setIcon(new ImageIcon(tx));
						}
						System.out.println(tx);
					} catch (Exception e) {
						// TODO 自动生成的 catch 块
						e.printStackTrace();
					}
					radioButton_1.setSelected(false);
					radioButton_2.setSelected(false);
				}
			}
		});
		radioButton.setBounds(146, 326, 72, 41);
		contentPane.add(radioButton);
		
		radioButton_1 = new JRadioButton("\u6559\u5E08");
		radioButton_1.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent arg0) {
				if(radioButton_1.isSelected()){
					label.setIcon(new ImageIcon("C:\\Users\\GUOJI\\Desktop\\javas\\de1234.png"));
					TeacherDao td =new TeacherDao();
					textField_1.setText(passwordField.getText());
					try {
						String tx = td.toxiang(textField.getText(),textField_1.getText());
						if(!tx.equals("")){
							label.setIcon(new ImageIcon(tx));
						}
						System.out.println(tx);
					} catch (Exception e) {
						// TODO 自动生成的 catch 块
						e.printStackTrace();
					}
					radioButton.setSelected(false);
					radioButton_2.setSelected(false);
				}
			
			}
		});
		radioButton_1.setBounds(232, 326, 72, 41);
		contentPane.add(radioButton_1);
		
		radioButton_2 = new JRadioButton("\u7BA1\u7406\u5458");
		radioButton_2.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent arg0) {
				if(radioButton_2.isSelected()){
					label.setIcon(new ImageIcon("C:\\Users\\GUOJI\\Desktop\\javas\\de1234.png"));
					radioButton.setSelected(false);
					radioButton_1.setSelected(false);
				}
			}
		});
		radioButton_2.setBounds(320, 326, 90, 41);
		contentPane.add(radioButton_2);
		
		JButton button = new JButton("\u786E\u8BA4");
		button.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent arg0) {
				if(!radioButton.isSelected()&&!radioButton_1.isSelected()&&!radioButton_2.isSelected()){
					JOptionPane.showMessageDialog(null,"请选择登录方式");
				}
				if(radioButton.isSelected()){
					StudentDao sd =new StudentDao();
					textField_1.setText(passwordField.getText());
					try {
						String tx = sd.toxiang(textField.getText(),textField_1.getText());
						if(!tx.equals("")){
							id = textField.getText();
							JOptionPane.showMessageDialog(null,"成功");
							 DenLu.this.dispose();
							 Student_view sc = new Student_view();
							 sc.setVisible(true);
						}
						else{
							JOptionPane.showMessageDialog(null,"失败：请查看账户和密码是否正确");
						}
					} catch (Exception e) {
						// TODO 自动生成的 catch 块
						e.printStackTrace();
					}
				}
				//教师
				if(radioButton_1.isSelected()){
					TeacherDao td =new TeacherDao();
					textField_1.setText(passwordField.getText());
					try {
						String tx = td.toxiang(textField.getText(),textField_1.getText());
						if(!tx.equals("")){
							id = textField.getText();
							JOptionPane.showMessageDialog(null,"成功");
							 DenLu.this.dispose();
							 Teacher_view sc = new Teacher_view();
							 sc.setVisible(true);
						}
						else{
							JOptionPane.showMessageDialog(null,"失败：请查看账户和密码是否正确");
						}
					} catch (Exception e) {
						// TODO 自动生成的 catch 块
						e.printStackTrace();
					}
				
				}
				//管理员
				if(radioButton_2.isSelected()){
					
					AdminDao td =new AdminDao();
					textField_1.setText(passwordField.getText());
					try {
						String tx = td.toxiangAdmin(textField.getText(),textField_1.getText());
						if(!tx.equals("")){
							JOptionPane.showMessageDialog(null,"成功");
							 DenLu.this.dispose();
							 Main sc = new Main();
							 sc.setVisible(true);
						}
						else{
							JOptionPane.showMessageDialog(null,"失败：请查看账户和密码是否正确");
						}
					} catch (Exception e) {
						// TODO 自动生成的 catch 块
						e.printStackTrace();
					}	
				}	
			}
		});
		button.setBounds(66, 383, 113, 27);
		contentPane.add(button);
		
		JButton button_1 = new JButton("\u9000\u51FA");
		button_1.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent arg0) {
				System.exit(0);
			}
		});
		button_1.setBounds(297, 383, 113, 27);
		contentPane.add(button_1);
		
		final JCheckBox checkBox = new JCheckBox("\u663E\u793A");
		checkBox.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent arg0) {
				if(checkBox.isSelected()){
					textField_1.setVisible(true);
					textField_1.setText(passwordField.getText());
					passwordField.setVisible(false);
				}
				else{
					textField_1.setVisible(false);
					passwordField.setText(textField_1.getText());
					passwordField.setVisible(true);
				}
			}
		});
		checkBox.setBounds(398, 294, 59, 27);
		contentPane.add(checkBox);
		
		JMenuItem menuItem = new JMenuItem("\u5FD8\u8BB0\u5BC6\u7801");
		menuItem.setForeground(Color.RED);
		menuItem.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent arg0) {
				 DenLu.this.dispose();
				 UpdatePasswd sc = new UpdatePasswd();
				 sc.setVisible(true);
			}
		});
		menuItem.setBounds(411, 413, 120, 24);
		contentPane.add(menuItem);
	}
		public static String getId(){
			return id;	
		}
}
	
