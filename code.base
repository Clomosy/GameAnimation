var 
  MyForm:TclGameForm;
  myGameEngine:TclGameEngine;
  GameTimer:TClTimer;
  BtnRandomFire:TclButton;
  geribtn : TClProButton;
  ImgBack:TclProImage;
  ImgTank:TclProImage;
  SndFire:Integer;
  //GameLoop:TclTimer;
  tPosX,tPosY:Single;
  
  procedure geriprcdr
  begin
  TclProButton(MyForm.clFindComponent('BtnGoBack')).Click;
  end;
  
  Procedure BtnRandomFireClick;
  var 
    i:Integer;
  begin
    MyForm.AnimationWidth := 75; 
    MyForm.AnimationHeight := 75;
    MyForm.clAnimateBitmap.AnimationCount :=9;
    MyForm.clAnimateBitmap.AnimationRowCount:=3;
    MyForm.clAnimateBitmap.Delay := 10;
    MyForm.clAnimateBitmap.Duration := 2;
    For i:=0 to 5 do
    Begin
      MyForm.clAnimateBitmap.Delay := Random()*10;
      MyForm.clAnimation(Random() * TForm(MyForm).ClientWidth, Random() * TForm(MyForm).ClientHeight, 0, 'Explosion.png');
    End;
    MyForm.PlayGameSound(SndFire);
  End;
  Procedure ProcOnGameTimer;
  begin
    ImgTank.Visible := True;
    tPosY := tPosY - 10;
    ImgTank.Position.X := tPosX;
    ImgTank.Position.Y := tPosY;
    if tPosY = -40 then
    begin
      ImgTank.Position.X := tPosX;
      ImgTank.Position.Y := 250;
      tPosY := 250;
    end;
  End;
begin
  MyForm := TclGameForm.Create(Self);
  MyForm.AddGameAssetFromUrl('https://www.clomosy.com/game/assets/BackImage.jpg');
  MyForm.AddGameAssetFromUrl('https://www.clomosy.com/game/assets/Fire.wav');
  MyForm.AddGameAssetFromUrl('https://www.clomosy.com/game/assets/Explosion.png');//animation
  MyForm.AddGameAssetFromUrl('https://www.clomosy.com/game/assets/TankMove.png');//animation
  MyForm.AddGameAssetFromUrl('https://www.clomosy.com/game/assets/Tank.png');
  
  tPosX := Random()* TForm(MyForm).ClientWidth;
  tPosY := TForm(MyForm).ClientHeight;
  SndFire := MyForm.RegisterSound('Fire.wav');
  MyForm.SoundIsActive:=True;

  ImgBack := MyForm.AddNewProImage(MyForm,'ImgBack');
  ImgBack.clSetImage('BackImage.jpg');
  //ImgBack.Properties.AutoSize := True;
  ImgBack.Align := alClient;
  //ImgBack.Visible := False;
  
  ImgTank := MyForm.AddNewProImage(MyForm,'ImgTank');
  ImgTank.clSetImage('Tank.png');
  ImgTank.Properties.AutoSize := False;
  ImgTank.Width := ImgTank.Width * 2;
  ImgTank.Height := ImgTank.Height * 2;
  ImgTank.Visible := False;
  tPosY:= ImgTank.Top;
  tPosX:= ImgTank.Left;
  ImgTank.Align:= alNone;

  BtnRandomFire:= MyForm.AddNewButton(MyForm,'BtnRandomFire','RANDOM FIRE');
  MyForm.AddNewEvent(BtnRandomFire,tbeOnClick,'BtnRandomFireClick');
  BtnRandomFire.Height := 70;
  BtnRandomFire.Align := alBottom;
  BtnRandomFire.Margins.Bottom := 40;
  
  geribtn := MyForm.AddNewProButton(MyForm,'geribtn','');
  clComponent.SetupComponent(geribtn,'{"Align" : "None","Width":70,"Height":50,"ImgUrl":"https://img.icons8.com/flat-round/64/circled-left.png"}');
  MyForm.AddNewEvent(geribtn,tbeOnClick,'geriprcdr');
  geribtn.Position.X:=5;
  geribtn.Position.Y:=7;
  
  GameTimer:= MyForm.AddNewTimer(MyForm,'GameTimer',1000);
  GameTimer.Interval := 500;//36 m.saniye aralıklarla 
  GameTimer.Enabled := True;
  MyForm.AddNewEvent(GameTimer,tbeOnTimer,'ProcOnGameTimer');
  

  MyForm.Run;
End;