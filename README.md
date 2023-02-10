# Cronometro
 
unit Unit1;

interface

uses
  Winapi.Windows, Winapi.Messages, System.SysUtils, System.Variants, System.Classes, Vcl.Graphics,
  Vcl.Controls, Vcl.Forms, Vcl.Dialogs, Vcl.StdCtrls, Vcl.ExtCtrls, Vcl.Buttons,
  DateUtils;

type
  TForm1 = class(TForm)
    Timer1: TTimer;
    Panel3: TPanel;
    Panel1: TPanel;
    Panel2: TPanel;
    Shape1: TShape;
    Panel4: TPanel;
    Shape2: TShape;
    btnIniciar: TSpeedButton;
    btnMarcar: TSpeedButton;
    Panel5: TPanel;
    Label1: TLabel;
    pnlMarcação: TPanel;
    Panel6: TPanel;
    Panel7: TPanel;
    Panel8: TPanel;
    Panel9: TPanel;
    ListBox2: TListBox;
    Panel10: TPanel;
    ListBox1: TListBox;
    procedure btnIniciarClick(Sender: TObject);
    procedure Timer1Timer(Sender: TObject);
    procedure btnMarcarClick(Sender: TObject);
  private
    { Private declarations }
  public
    contador:integer
  end;

var
  Form1: TForm1;

implementation

{$R *.dfm}

procedure TForm1.btnIniciarClick(Sender: TObject);
begin
  if (btnIniciar.Caption = 'Iniciar') then
  begin
    pnlMarcação.Visible:= false;
    label1.Caption:= '00:00:00';

    //iniciar o timer
    Timer1.Enabled:= true;

    //exibe o botao de marcar
    Timer1.enabled:= true;

    //alterar descriçaão do label
     btnIniciar.Caption:= 'Parar';

     // o botão de marcar
     btnMarcar.visible:= true;

     //define a variavel contadora pra 1
     contador :=1;

     //esconde o painel de marcações
     panel2.visible:=true;

     listbox1.clear;
     listbox2.clear;

      end
      else if(btnIniciar.Caption='Parar') then
      begin
        Timer1.Enabled:=false;
        btnMarcar.Visible:=false;
        btnIniciar.Caption:= 'Iniciar';
        panel2.Visible:=false;
      end;
end;

procedure TForm1.btnMarcarClick(Sender: TObject);
  var id:string;
begin
  pnlMarcação.visible:=true;
  id:= inttostr(contador);
  listbox1.Items.Add(id);
  listbox2.items.add(label1.Caption);
  contador:= contador+1
end;

procedure TForm1.Timer1Timer(Sender: TObject);
var
  tempo: Ttime;
begin
   //Converte o texto do label de tempo em texto
   tempo := StrtoTime(label1.caption);
   //adiciona um segundo na variavel
   tempo:=IncSecond(tempo,1);
   label1.Caption:= timetostr(tempo);
end;

end.
