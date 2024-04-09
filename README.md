# javaProyecto
Programa que pide 3 coordenadas de los vértices de un triángulo para indicar su perímetro y área, así como determinar el tipo de triángulo.
import javax.swing.JOptionPane;

public class EvaluacionMate {

    public static void main(String[] args) {
        int x1, y1, x2, y2, x3, y3;
        double lado1, lado2, lado3;
        double peri;
        double area;
        double ang1, ang2, ang3;
        double semi;
        
        x1 = Integer.parseInt(JOptionPane.showInputDialog("Teclea la coordenada x del 1er vértice:"));
        y1 = Integer.parseInt(JOptionPane.showInputDialog("Teclea la coordenada y del 1er vértice:"));
        x2 = Integer.parseInt(JOptionPane.showInputDialog("Teclea la coordenada x del 2do vértice:"));
        y2 = Integer.parseInt(JOptionPane.showInputDialog("Teclea la coordenada y del 2do vértice:"));
        x3 = Integer.parseInt(JOptionPane.showInputDialog("Teclea la coordenada x del 3er vértice:"));
        y3 = Integer.parseInt(JOptionPane.showInputDialog("Teclea la coordenada y del 3er vértice:"));
        
        lado1 = calcularDistancia(x1, y1, x2, y2);
        lado2 = calcularDistancia(x2, y2, x3, y3);
        lado3 = calcularDistancia(x3, y3, x1, y1);
        
        peri = lado1 + lado2 + lado3;
        
        semi = peri/2;
        area = Math.sqrt(semi*(semi-lado1)*(semi-lado2)*(semi-lado3));
        
        ang1=Math.acos((lado2*lado2+lado3*lado3-lado1*lado1)/(2*lado2*lado3));
        ang2=Math.acos((lado1*lado1+lado3*lado3-lado2*lado2)/(2*lado1*lado3));
        ang3=Math.acos((lado1*lado1+lado2*lado2-lado3*lado3)/(2*lado1*lado2));
        
        ang1=Math.toDegrees(ang1);
        ang2=Math.toDegrees(ang2);
        ang3=Math.toDegrees(ang3);
        
        String tipoTriangulo;
        if (lado1==lado2 && lado2==lado3) {
            tipoTriangulo="Equilátero";
        } else if (lado1==lado2 || lado2==lado3 || lado1==lado3) {
            tipoTriangulo="Isósceles";
        } else {
            tipoTriangulo="Escaleno";
        }
        JOptionPane.showMessageDialog(null,
                "Triángulo: "+tipoTriangulo+ 
                        "\n Perímetro: "+peri+ 
                        "\n Área: "+area+ 
                        "\n 1er Ángulo: "+ang1+" grados"+
                        "\n 2do Ángulo 2: " +ang2+" grados"+
                        "\n 3er Ángulo 3: " +ang3+" grados");
    }
    
    public static double calcularDistancia(int x1, int y1, int x2, int y2) {
        return Math.sqrt(Math.pow(x2 - x1, 2) + Math.pow(y2 - y1, 2));
    }
}
