# cs-form-framework-combobox
一般的な key と value でコンボボックスを利用する

```cs
this.comboBox1.DropDownStyle = System.Windows.Forms.ComboBoxStyle.DropDownList;
```

```cs
// ******************************
// コンボボックスに追加情報
// をセットする為のクラス
// ******************************
private class ComboData {

    public ComboData(string Text, string Data) {
        this.Text = Text;
        this.Data = Data;
    }

    public string Text { get; set; }
    public string Data { get; set; }

    public override string ToString() {
        return this.Text;
    }
}
```

```cs
private void Form1_Load(object sender, EventArgs e) {

    // ComboData を コンボボックスにセット
    comboBox1.Items.Clear();
    comboBox1.Items.Add(new ComboData("昨日", "0001"));
    comboBox1.Items.Add(new ComboData("今日", "0002"));
    comboBox1.Items.Add(new ComboData("明日", "0003"));
    // 非選択状態
    comboBox1.SelectedIndex = -1; 

}

private void comboBox1_SelectedIndexChanged(object sender, EventArgs e) {

    ComboBox cb = (ComboBox)sender;

    // コンボボックスのテキスト
    Debug.WriteLine(cb.Text);
    // コンボボックスの選択インデックス
    int idx = cb.SelectedIndex;
    Debug.WriteLine(idx);

    // 選択されていた場合は、Items コレクションでテキストとデータを表示
    if (idx != -1) {
        ComboData cdata = (ComboData)cb.Items[idx];

        Debug.WriteLine(cdata.Text);
        Debug.WriteLine(cdata.Data);
    }
}
```
