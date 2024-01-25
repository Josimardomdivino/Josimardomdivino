import java.util.ArrayList;

class Barco {
    int numero;
    String nome;
    int anoFabricacao;

    Barco(int numero, String nome, int anoFabricacao) {
        this.numero = numero;
        this.nome = nome;
        this.anoFabricacao = anoFabricacao;
    }
}

class Regata {
    int numero;
    String data;
    String horaInicio;
    Barco vencedor;
    ArrayList<Barco> participantes = new ArrayList<>();

    Regata(int numero, String data, String horaInicio) {
        this.numero = numero;
        this.data = data;
        this.horaInicio = horaInicio;
    }

    void addParticipante(Barco barco) {
        if (participantes.size() < 4 && !participantes.contains(barco)) {
            participantes.add(barco);
        }
    }

    void setVencedor(Barco barco) {
        vencedor = barco;
    }
}

public class RegataProgram {
    public static ArrayList<Barco> barcos = new ArrayList<>();
    public static ArrayList<Regata> regatas = new ArrayList<>();

    public static void cadBarco(int numero, String nome, int anoFabricacao) {
        for (Barco barco : barcos) {
            if (barco.numero == numero) {
                System.out.println("Ih, já tem um barco com esse número.");
                return;
            }
        }
        barcos.add(new Barco(numero, nome, anoFabricacao));
        System.out.println("Blz, cadastrei o barco " + nome + "!");
    }

    public static void cadRegata(int numero, String data, String horaInicio) {
        for (Regata regata : regatas) {
            if (regata.numero == numero) {
                System.out.println("Oi, já teve essa regata.");
                return;
            }
        }
        regatas.add(new Regata(numero, data, horaInicio));
        System.out.println("Sucesso! Cadastrei a regata " + numero + ".");
    }

    public static void main(String[] args) {
        cadBarco(1, "BarcoA", 2020);
        cadBarco(2, "BarcoB", 2019);

        cadRegata(101, "2024-01-24", "14:00");
        cadRegata(102, "2024-02-01", "15:30");
    }
}
