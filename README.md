# SoftwareEngineering
package buttondemo;

import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
import javax.swing.event.*;


public class ButtonDemo implements ActionListener {

    int k = 0;
    JLabel jlab;
    JLabel jlabWhat;
    JLabel jlabSB;
    JLabel jlabText;
    JRadioButton jrbFirst;
    JRadioButton jrbSecond;
    JRadioButton jrbThird;
    JSlider jsb;
    JScrollPane jscrlp;

    ButtonDemo() {
        JFrame jfrm = new JFrame("Задача 16");
        jfrm.getContentPane().setLayout(new GridLayout(4,1));
        jfrm.setSize(900, 500);
        jfrm.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        JButton jbtnFirst = new JButton("Кнопка");


        jfrm.getContentPane().add(jbtnFirst);

        jlab = new JLabel("Нажмите кнопку.");
        jlabWhat = new JLabel("Выбрана радиокнопка: Первая");
        jlabSB = new JLabel("Значение ползунка: ");
        jlabText = new JLabel("<html>Привет<br>" +
                "Таким образом<br>" +
                "проводится демонстрация задачи<br>" +
                "по программированию<br>" +
                "с использованием прокручиваемой областью текста<br>" +
                 /*"...<br>"+
                "...<br>"+
                "...<br>"+
                "...<br>"+
                "...<br>"+*/
                "Конец введенного текста.");
        jrbFirst= new JRadioButton("Первая",true);
        jrbSecond= new JRadioButton("Вторая");
        jrbThird= new JRadioButton("Третья");
        jsb = new JSlider(Adjustable.HORIZONTAL);
        jscrlp = new JScrollPane(jlabText);
        ButtonGroup bg = new ButtonGroup();
        bg.add(jrbFirst);
        bg.add(jrbSecond);
        bg.add(jrbThird);
        jrbFirst.setEnabled(true);
        jrbSecond.setEnabled(true);
        jrbThird.setEnabled(true);
        jrbFirst.addActionListener(this);
        jrbSecond.addActionListener(this);
        jrbThird.addActionListener(this);
        jbtnFirst.addActionListener(this);
        jscrlp.setVerticalScrollBarPolicy(JScrollPane.VERTICAL_SCROLLBAR_ALWAYS);
        jsb.addChangeListener(new ChangeListener(){
            public void stateChanged(ChangeEvent e){
                jlabSB.setText("Значение ползунка: "+ jsb.getValue());
            }
        });
        jfrm.getContentPane().add(jlab);
        jfrm.getContentPane().add(jrbFirst);
        jfrm.getContentPane().add(jrbSecond);
        jfrm.getContentPane().add(jrbThird);
        jfrm.getContentPane().add(jlabWhat);
        jfrm.getContentPane().add(jlabSB);
        jfrm.getContentPane().add(jsb);
        jfrm.getContentPane().add(jscrlp);
        jfrm.setVisible(true);
    }

    public void actionPerformed(ActionEvent ae) {
        String opts = "";
        if(jrbFirst.isSelected()) opts = "Первая";
        else if(jrbSecond.isSelected()) opts = "Вторая";
        else opts = "Третья";

        if (ae.getActionCommand().equals("Кнопка"))
            k++;

        jlabWhat.setText("Выбрана радиокнопка  "+opts);

        jlab.setText("Кнопка нажата  " + k + " раз");

    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(new Runnable() {
            public void run() {
                new ButtonDemo() {
                };
            }
        });
    }

}
