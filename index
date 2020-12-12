<!DOCTYPE html>
<html>

<head>
    <title>Cetak Faktur Penjualan</title>
    <style type="text/css" media="print">
    @page {
        size: auto;
        margin: 0mm;
    }

    .dontPrint {
        display: none;
    }
    </style>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.1/jquery.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jsbarcode/3.8.0/JsBarcode.all.js"></script>
    <style type="text/css">
    @media print {
        .pagebreak {
            page-break-before: always;
        }

        /* page-break-after works, as well */
    }

    @font-face {
        font-family: "Code 128 Reguler";
        src: url('code128.ttf');
    }

    .barcode {
        font-size: 15mm;
    }

    p {
        font-size: 12px;
    }
    }
    </style>
</head>

<body onload="window.print()">
    <?php $kode_toko = $this->session->userdata('kode_toko'); ?>
    <?php
	$feedback = json_decode($DataFaktur);
	// var_dump($feedback->data);
	if ($feedback == null) {
		redirect('Penjualan/TransaksiPenjualan');
	}
	foreach ($feedback->data as $row) :
	?>

    <div class="header" style="position: relative;top:45px;left:560px;width: 200px;">
        <p>
            Tanggal : <?= $row->tgl_faktur_jual ?><br>
            Nama: <?= $row->nama_customer ?><br>
            Alamat: <?= $row->alamat_customer ?></p>
    </div>

    <div class="gambar" style="position: relative;top: 87px;left: 648px;width: 10px;">
        <img src="<?= base_url('./assets/images/NsiPic/' . $kode_toko . '/' . $row->input_date . '/' . $row->kode_barang . '.jpg'); ?>"
            height="128px" width="120px">
    </div>

    <div class="kode_barcode" style="position: relative;left: 20px;top: -30px;width: 100px;">
        <p><?= $row->kode_barcode ?></p>
    </div>
    <div class="qty" style="position: relative;top: -56px;left:116px;width: 10px;">
        <p>1</p>
    </div>
    <div class="nama_barang" style="width: 300px;position: relative;top: -84px;left: 115px;text-align: center;">
        <p><?= $row->nama_barang ?><br>
            <?= $row->nama_atribut ?></p>
    </div>
    <div class="kadar" style="position: relative;left: 420px;top: -122px;width: 50px;">
        <p><?= $row->kadar ?></p>
    </div>
    <div class="berat" style="position: relative;left: 480px;top: -148px;width: 80px;">
        <p><?= $row->berat ?></p>
    </div>
    <div class="harga" style="position: relative;left: 488px;top: -174px;width: 200px;text-align: center;">
        <p><?= number_format($row->harga_rp) ?><br>
        <p><?= $row->harga_atribut==0 ? '' : number_format($row->harga_atribut) ?></p>
    </div>
    </td>
    </div>
    <div class="kode_barcode_gambar" style="position: relative;top: -184px;left: 174px;width: 100px;">
        <?php $barcode = $row->kode_barcode ?>
        <img id="barcode<?= $row->kode_barcode ?>" class="barcode">
    </div>

    <div class="ongkos" style="position: relative;left: 519px;width:100px;top: -238px;">
        <p><?= $row->ongkos==0 ? '-' : number_format($row->ongkos) ?></p>
    </div>
    <div class="total_rp" style="position: relative;left: 527px;top:-226px;width: 200px;">
        <p><?= rupiah($row->total_rp) ?></p>
    </div>
    <div class="no_faktur" style="position: relative;left:624px; top: -187px;width: 200px;">
        <p><?= $row->no_faktur_jual ?> </p>
    </div>
    <div class="nama_sales" style="position: relative;left:624px; top:-235px;width:100px">
        <p><?= $row->nama_sales ?> </p>
    </div>
    <script>
    $("#barcode<?= $row->kode_barcode ?>").JsBarcode("<?= $barcode ?>", {
        width: 2,
        height: 15
    });
    </script>
    <div class="pagebreak"> </div>
    <?php endforeach; ?>

    <table>
        <tr>
            <td>
                <font color="red" class="lebar dontPrint">
                    <p>
                        <!-- -----        Tekan F5 Untuk Kembali     ----- <br> -->
                        ----- Tekan (CTR+P) Untuk Print Priview -----<br>
                    </p>
                </font>
            </td>
        </tr>
    </table>
</body>
</html>
