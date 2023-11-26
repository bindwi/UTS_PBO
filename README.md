import java.util.ArrayList;
import java.util.Scanner;

class Transaksi {
    private String keterangan;
    private double jumlah;

    public Transaksi(String keterangan, double jumlah) {
        this.keterangan = keterangan;
        this.jumlah = jumlah;
    }

    public String getKeterangan() {
        return keterangan;
    }

    public double getJumlah() {
        return jumlah;
    }
}

class CatatanKeuangan {
    private ArrayList<Transaksi> transaksiList;

    public CatatanKeuangan() {
        transaksiList = new ArrayList<>();
    }

    public void tambahTransaksi(Transaksi transaksi) {
        transaksiList.add(transaksi);
    }

    public ArrayList<Transaksi> getTransaksiList() {
        return transaksiList;
    }
}

class CatatanKeuanganView {
    public void tampilkanCatatanKeuangan(ArrayList<Transaksi> transaksiList) {
        System.out.println("Catatan Keuangan:");

        for (Transaksi transaksi : transaksiList) {
            System.out.println("Keterangan: " + transaksi.getKeterangan());
            System.out.println("Jumlah: " + transaksi.getJumlah());
            System.out.println("---------------");
        }
    }
}

class CatatanKeuanganController {
    private CatatanKeuangan catatanKeuangan;
    private CatatanKeuanganView catatanKeuanganView;

    public CatatanKeuanganController(CatatanKeuangan catatanKeuangan, CatatanKeuanganView catatanKeuanganView) {
        this.catatanKeuangan = catatanKeuangan;
        this.catatanKeuanganView = catatanKeuanganView;
    }

    public void tambahTransaksi(String keterangan, double jumlah) {
        Transaksi transaksi = new Transaksi(keterangan, jumlah);
        catatanKeuangan.tambahTransaksi(transaksi);
    }

    public void tampilkanCatatanKeuangan() {
        ArrayList<Transaksi> transaksiList = catatanKeuangan.getTransaksiList();
        catatanKeuanganView.tampilkanCatatanKeuangan(transaksiList);
    }
}

public class Main {
    public static void main(String[] args) {
        CatatanKeuangan catatanKeuangan = new CatatanKeuangan();
        CatatanKeuanganView catatanKeuanganView = new CatatanKeuanganView();
        CatatanKeuanganController catatanKeuanganController = new CatatanKeuanganController(catatanKeuangan, catatanKeuanganView);
        catatanKeuanganController.tambahTransaksi("Belanja bulanan", -500.0);
        catatanKeuanganController.tambahTransaksi("Gaji", 2000.0);
        catatanKeuanganController.tambahTransaksi("Makan di luar", -50.0);
        catatanKeuanganController.tampilkanCatatanKeuangan();
    }
}
