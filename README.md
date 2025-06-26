---------------translate kotuval---------------------------------


import javax.swing.*;
import java.awt.*;

public class Translation extends JPanel {

  
    protected void paintComponent(Graphics g) {
        super.paintComponent(g); // Ensures proper rendering

        int[] x = {0, 200, 200, 0}; // X-coordinates
        int[] y = {0, 0, 200, 200}; // Y-coordinates
        // Original square
        g.setColor(Color.BLUE);
        ddaLine(x[0], y[0], x[1], y[1], g);
        ddaLine(x[1], y[1], x[2], y[2], g);
        ddaLine(x[2], y[2], x[3], y[3], g);
        ddaLine(x[3], y[3], x[0], y[0], g);

        // Translated square
        
        translate(x, y, 250, 250); // Translate by (20, 20)

        g.setColor(Color.RED);
        ddaLine(x[0], y[0], x[1], y[1], g);
        ddaLine(x[1], y[1], x[2], y[2], g);
        ddaLine(x[2], y[2], x[3], y[3], g);
        ddaLine(x[3], y[3], x[0], y[0], g);
    }

    public void ddaLine(int x1, int y1, int x2, int y2, Graphics g) {
        int dx = x2 - x1;
        int dy = y2 - y1;

        int steps = Math.max(Math.abs(dx), Math.abs(dy));

        float Xinc = (float) dx / steps;
        float Yinc = (float) dy / steps;

        float x = x1;
        float y = y1;

        for (int i = 0; i <= steps; i++) {
            g.fillRect(Math.round(x), Math.round(y), 1, 1);
            x += Xinc;
            y += Yinc;
        }
    }

    public void translate(int x[], int y[], int tx, int ty) {
        for (int i = 0; i < x.length; i++) {
            x[i] += tx;
            y[i] += ty;
        }
    }

    public static void main(String[] args) {
        JFrame frame = new JFrame("Translation Example");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(600, 600);
        frame.add(new Translation());
        frame.setVisible(true);
    }
}

-----------------------------scaling---------------------------------


import javax.swing.*;
import java.awt.*;

public class Scaling extends JPanel {

    @Override
    protected void paintComponent(Graphics g) {
        super.paintComponent(g);

        
        int[] x = {0, 200, 200, 0};
        int[] y = {0, 0, 200, 200};

       
        g.setColor(Color.BLUE);
        drawPolygon(x, y, g);

        
        float sx = 1.5f; // X-scaling factor
        float sy = 0.5f; // Y-scaling factor
        scale(x, y, sx, sy);

       
        g.setColor(Color.RED);
        drawPolygon(x, y, g);
    }
   
        private void drawPolygon(int[] x, int[] y, Graphics g) {
            for (int i = 0; i < x.length - 1; i++) {
                ddaLine(x[i], y[i], x[i + 1], y[i + 1], g);
            }
            // Close the polygon
            ddaLine(x[x.length - 1], y[y.length - 1], x[0], y[0], g);
        }
    
   

    public void ddaLine(int x1, int y1, int x2, int y2, Graphics g) {
        int dx = x2 - x1;
        int dy = y2 - y1;

        int steps = Math.max(Math.abs(dx), Math.abs(dy));

        float Xinc = (float) dx / steps;
        float Yinc = (float) dy / steps;

        float x = x1;
        float y = y1;

        for (int i = 0; i <= steps; i++) {
            g.fillRect(Math.round(x), Math.round(y), 1, 1);
            x += Xinc;
            y += Yinc;
        }
    }

    public void scale(int[] x, int[] y, float sx, float sy) {
        for (int i = 0; i < x.length; i++) {
            x[i] = Math.round(x[i] * sx);
            y[i] = Math.round(y[i] * sy);
        }
    }

    public static void main(String[] args) {
        JFrame frame = new JFrame("Scaling Example");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(600, 600);
        frame.add(new Scaling());
        frame.setVisible(true);
    }



---------------------------------rotation------------------------------

import javax.swing.*;
import java.awt.*;

public class Rotate extends JPanel {

    @Override
    protected void paintComponent(Graphics g) {
        super.paintComponent(g); // Ensures proper rendering

        // Original square coordinates
        int[] x = {100, 300, 300, 100};
        int[] y = {100, 100, 300, 300};

        // Draw original square in BLUE
        g.setColor(Color.BLUE);
        drawPolygon(x, y, g);


        // Apply rotation (relative to origin)
        double angle = Math.toRadians(30); // 60 degrees
        rotate(x, y, angle);

        // Draw transformed square in RED
        g.setColor(Color.RED);
        drawPolygon(x, y, g);
    }

    private void drawPolygon(int[] x, int[] y, Graphics g) {
        for (int i = 0; i < x.length - 1; i++) {
            ddaLine(x[i], y[i], x[i + 1], y[i + 1], g);
        }
        // Close the polygon
        ddaLine(x[x.length - 1], y[y.length - 1], x[0], y[0], g);
    }

    public void ddaLine(int x1, int y1, int x2, int y2, Graphics g) {
        int dx = x2 - x1;
        int dy = y2 - y1;

        int steps = Math.max(Math.abs(dx), Math.abs(dy));

        float Xinc = (float) dx / steps;
        float Yinc = (float) dy / steps;

        float x = x1;
        float y = y1;

        for (int i = 0; i <= steps; i++) {
            g.fillRect(Math.round(x), Math.round(y), 1, 1);
            x += Xinc;
            y += Yinc;
        }
    }

    public void rotate(int[] x, int[] y, double angle) {
        for (int i = 0; i < x.length; i++) {
            int oldX = x[i];
            int oldY = y[i];
            x[i] = Math.round((float)(oldX * Math.cos(angle) - oldY * Math.sin(angle)));
            y[i] = Math.round((float)(oldX * Math.sin(angle) + oldY * Math.cos(angle)));
        }
    }

    public static void main(String[] args) {
        JFrame frame = new JFrame("Scaling and Rotation Example");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(600, 600);
        frame.add(new Rotate());
        frame.setVisible(true);
    }
}

--------------------------------sharering-----------------------------


import javax.swing.*;
import java.awt.*;

public class Shearing extends JPanel {

    @Override
    protected void paintComponent(Graphics g) {
        super.paintComponent(g); // Ensures proper rendering

        // Original square
        g.setColor(Color.BLUE);
        // Square coordinates
        int[] x = {0, 200, 200, 0}; // X-coordinates
        int[] y = {0, 0, 200, 200}; // Y-coordinates
        ddaLine(x[0], y[0], x[1], y[1], g);
        ddaLine(x[1], y[1], x[2], y[2], g);
        ddaLine(x[2], y[2], x[3], y[3], g);
        ddaLine(x[3], y[3], x[0], y[0], g);
       

        // Shear the square
       //shear(x, y, 1.0f, 0.5f); // Shear X by 1.0, Y by 0.5
       //shear(x, y, 0, 0.5f); // Shear X by 0, Y by 0.5
        shear(x, y, 1.0f, 0); // Shear X by 1.0, Y by 0

        // Draw sheared square
        g.setColor(Color.RED);
        ddaLine(x[0], y[0], x[1], y[1], g);
        ddaLine(x[1], y[1], x[2], y[2], g);
        ddaLine(x[2], y[2], x[3], y[3], g);
        ddaLine(x[3], y[3], x[0], y[0], g);
    }

    public void ddaLine(int x1, int y1, int x2, int y2, Graphics g) {
        int dx = x2 - x1;
        int dy = y2 - y1;
        int steps = Math.max(Math.abs(dx), Math.abs(dy));

        float Xinc = (float) dx / steps;
        float Yinc = (float) dy / steps;

        float x = x1;
        float y = y1;

        for (int i = 0; i <= steps; i++) {
            g.fillRect(Math.round(x), Math.round(y), 1, 1);
            x += Xinc;
            y += Yinc;
        }
    }

    public void shear(int[] x, int[] y, float shx, float shy) {
        for (int i = 0; i < x.length; i++) {
            int newX = Math.round(x[i] + shx * y[i]);
            int newY = Math.round(y[i] + shy * x[i]);
            x[i] = newX;
            y[i] = newY;
        }
    }

    public static void main(String[] args) {
        JFrame frame = new JFrame("2D Shearing Example");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(800, 800);
        frame.add(new Shearing());
        frame.setVisible(true);
    }
}

--------------------------------------------------------------------------------------------------

--------------------------------------lint drowing---------------------------------------------

  public void ddD(int x1,int y1,int x2,int y2,Graphics g ){

        int dx = x2-x1;
        int dy = y2-y1;

        int steps = Math.max(Math.abs(dx),Math.abs(dy));

        float x_inc = (float) dx / steps;
        float y_inc = (float) dy / steps;

        float x = x1;
        float y = y1;

        for(int i = 0; i<=steps;i++){

            g.fillRect(Math.round(x),Math.round(y),2,2);

            x += x_inc;
            y += y_inc;


        

        }


    }
    public void Translaon(int x[],int y[],int tx,int ty){

        for(int i = 0; i < x.length;i++){

            x[i] += tx;
            y[i] += ty;


        }

    }

----------------------------------crical algorithm------------------------------------------
