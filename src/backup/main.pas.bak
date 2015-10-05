unit Main;

{$mode objfpc}{$H+}

interface

uses
  Classes, SysUtils, FileUtil, Forms, Controls, Graphics, Dialogs, ExtCtrls,
  ComCtrls, Grids, StdCtrls;

type
  tKaM_House = (ht_ArmorSmithy, ht_ArmorWorkshop_Armor, ht_ArmorWorkshop_Shield, ht_Bakery, ht_Butcher, ht_CoalMine_Weapon, ht_CoalMine_Armor, ht_CoalMine_Gold, ht_Farm_Horse, ht_Farm_Swine, ht_Farm_Flour, ht_Fisher, ht_GoldMine, ht_IronMine_Armor, ht_IronMine_Weapon, ht_IronSmithy_Armor, ht_IronSmithy_Weapon, ht_Metallurgists, ht_Mill, ht_Quarry, ht_Sawmill_Shield, ht_Sawmill_Weapon, ht_School, ht_Stables, ht_Swine, ht_Tannery, ht_WeaponSmithy, ht_WeaponWorkshop, ht_Vineyard, ht_Woodcutters_Shield, ht_Woodcutters_Weapon, ht_Fish, ht_Fish_Sec, ht_Fish_Eat, ht_Wine, ht_Wine_Sec, ht_Wine_Eat, ht_Horse, ht_Loaf, ht_Loaf_Sec, ht_Loaf_Eat, ht_Sausage, ht_Sausage_Sec, ht_Sausage_Eat, ht_LArmor, ht_WShield, ht_WWeapon, ht_IArmor, ht_IWeapon, ht_Unit, ht_Stone);
  tKaM_House_Array = array of tKaM_House;
  tFrac = Record aNum, aDen: Int64; end;
  tDirection = (tToRaw, tFromRaw);
  tPlayerType = (tPlayer, tEnemy);
  tKaM_Warrior = (ut_Militia = 1, ut_AxeFighter, ut_SwordFighter, ut_Bowman, ut_Crossbowman, ut_LanceCarrier, ut_Pikeman, ut_Scout, ut_Knight);
  tBuildTimes = array[0..3] of Int64; //seconds
  tResources = (tGold, tIron, tCoal, tFertile);
  tOrder = array[0..2] of tResources; //0 lowest, 2 highest

  { TMainForm }

  TMainForm = class(TForm)
    CheckBox1, CheckBox2, CheckBox3, CheckBox4, CheckBox5, CheckBox6, CheckBox7, CheckBox8, CheckBox9, CheckBox10, CheckBox11, CheckBox12, CheckBox13, CheckBox14, CheckBox15: TCheckBox;
    ComboBox1, ComboBox2, ComboBox3, ComboBox4, ComboBox5, ComboBox6, ComboBox7, ComboBox8: TComboBox;
    Edit1, Edit10, Edit11, Edit12, Edit13, Edit14, Edit15, Edit16, Edit17, Edit18, Edit19, Edit2, Edit20, Edit21, Edit22, Edit23, Edit24, Edit25, Edit26, Edit27, Edit28, Edit29, Edit3, Edit30, Edit31, Edit32, Edit33, Edit34, Edit4, Edit5, Edit6, Edit7, Edit8, Edit9, Edit35, Edit36, Edit37, Edit38: TEdit;
    ImageCounters, ImageHitChance, ImageFight, ImageBack, ImageIWeapons, ImageWeapSmithy, ImageIArmor, ImageArmorSmithy, ImageIronSmithy, ImageIronMine, ImageCoalMine, ImageUnit, ImageSchool, ImageMetallurgist, ImageGoldMine, ImageCoalG, ImageIronM, ImageGoldM, ImageStoneM, ImageStone, ImageQuarry, ImageWWeapons, ImageWeapWorkshop, ImageFish, ImageWater, ImageFisherman, ImageGreenland, ImageWood, ImageSawmill, ImageWine, ImageField, ImageWineField, ImageVineyard, ImageHorse, ImageStable, ImageWShield, ImageLArmor, ImageArmorWorkshop, ImageTannery, ImageSausage, ImageButcher, ImageSwine, ImageLoaf, ImageBakery, ImageMill, ImageFarm, ImageUnit1, ImageUnit2, ImageUnit3, ImageUnit4: TImage;
    Label1, Label2, Label3, Label4, Label5, Label6, Label7, Label8, Label9, Label10, Label11, Label12, Label13, Label14, Label15, Label16, Label17, Label18, Label19, Label20, Label21, Label22, Label23, Label24, Label25, Label26, Label27, Label28, Label29, Label30, Label31, Label32, Label33, Label34, Label35, Label36: TLabel;
    LabeledEdit1, LabeledEdit2, LabeledEdit3, LabeledEdit4, LabeledEdit5, LabeledEdit6, LabeledEdit7, LabeledEdit8, LabeledEdit9, LabeledEdit10, LabeledEdit11, LabeledEdit12, LabeledEdit13, LabeledEdit14, LabeledEdit15, LabeledEdit16: TLabeledEdit;
    MainPanel: TPanel;
    Memo1: TMemo;
    PageControl: TPageControl;
    MainScrollBox: TScrollBox;
    Shape1, Shape2, Shape3, Shape4, Shape5, Shape6, Shape7, Shape8, Shape9, Shape10, Shape11, Shape12, Shape13, Shape14, Shape15, Shape16, Shape17, Shape18: TShape;
    StaticText1, StaticText10, StaticText11, StaticText12, FishFeed, WineFeed, LoafFeed, SausageFeed, StaticText2, StaticText3, StaticText4, StaticText5, StaticText6, StaticText7, StaticText8, StaticText9: TStaticText;
    StringGridStats, StringGridRecruited: TStringGrid;
    TabChains, TabUnits, TabFight, TabCounters: TTabSheet;
    MainTimer: TTimer;

    procedure CheckBox11EditingDone(Sender: TObject);
    function aSetCheckbox(aCheckBox: TCheckBox; aSender: TObject): Boolean;
    procedure CheckBoxEditingDone(Sender: TObject);
    procedure ComboBox1EditingDone(Sender: TObject);
    procedure ComboBox4Change(Sender: TObject);
    procedure ComboBox5Change(Sender: TObject);
    procedure ComboBox7Change(Sender: TObject);
    procedure ComboBox8Change(Sender: TObject);
    procedure FormCreate(Sender: TObject);
    function aGetIconName(aCol, aRow: Integer): String;
    procedure FormResize(Sender: TObject);
    procedure MainTimerTimer(Sender: TObject);
    procedure StringGrid1DrawCell(Sender: TObject; aCol, aRow: Integer;
      aRect: TRect; aState: TGridDrawState);
    procedure StringGridStatsDrawCell(Sender: TObject; aCol, aRow: Integer;
      aRect: TRect; aState: TGridDrawState);

    function aHouseToObject(aHouse: tKaM_House): TObject;
    function aObjectToHouse(aObj: TObject): tKaM_House;
    function aGetValue(aDir: tDirection; aHouse: tKaM_House): tFrac;
    function aGetHouses(aDir: tDirection; aHouse: tKaM_House): tKaM_House_Array;
    procedure aUpdateHouses;
    procedure EditRawDo(aHouse: tKaM_House);
    procedure EditWare(Sender: TObject);
    procedure EditRaw(Sender: TObject);
    procedure LabeledEdit15EditingDone(Sender: TObject);
    procedure LabeledEditEditingDonePlayer(Sender: TObject);
    procedure LabeledEditEditingDoneEnemy(Sender: TObject);
    procedure aDrawArrow(aWarriorPlayer, aWarriorEnemy: tKaM_Warrior);
    procedure aUpdateScheme;

  private
    var
      aGroupTypesStage: Word;
      aGroupTypesDraw: array[0..15] of Record aRect: TRect; aState: TGridDrawState; end;

      aHouseValue: array[Low(tKaM_House)..High(tKaM_House)] of tFrac;

  public

  end;

var
  MainForm: TMainForm;

  aLocs: array[Low(tPlayerType)..High(tPlayerType)] of Record
    aMaxMines, aDistance: array[Low(tResources)..High(tResources)] of tFrac;
  end;

  aEquipPhase: array[Low(tPlayerType)..High(tPlayerType)] of array[Low(tKaM_Warrior)..High(tKaM_Warrior)] of array[0..3] of Record
    aWhich: tResources;
    aRecruited, aDuration: Int64; //Number of recruited units is multiplied x1000, just in case... it won't matter anyway, since it's going to be used in a ratio.
  end;

  aStartTime, aTotalTime: Int64;

implementation

{$R *.lfm}

{ TMainForm }

function aMax(aVal1, aVal2: Int64): Int64;
begin
  if aVal1 > aVal2 then result := aVal1
  else result := aVal2;
end;

function aGetFrac(aNum, aDen: Int64): tFrac;
begin
  result.aNum := aNum;
  result.aDen := aDen;
end;

function aIsSameFrac(aF1, aF2: tFrac): Boolean;
begin
  result := (aF1.aNum = aF2.aNum) AND (aF1.aDen = aF2.aDen);
end;

function aSimplify(aFrac: tFrac): tFrac;
begin
  if aFrac.aDen = 0 then begin
    result.aNum := 0;
    result.aDen := 0;
  end else begin
    result.aNum := (aFrac.aNum*100000) div aFrac.aDen;

    if result.aNum mod 10 >= 5 then result.aNum := (result.aNum div 10)+1
    else result.aNum := result.aNum div 10;

    result.aDen := 10000;
  end;
end;

function aAddFracs(aF1, aF2: tFrac): tFrac;
begin
  if aF1.aDen = 0 then aF1.aDen := 1;
  if aF2.aDen = 0 then aF2.aDen := 1;

  result.aDen := aF1.aDen*aF2.aDen;
  result.aNum := aF1.aNum*aF2.aDen+aF2.aNum*aF1.aDen;
end;

function aMultFracs(aF1, aF2: tFrac): tFrac;
begin
  if aF1.aDen = 0 then aF1.aDen := 1;
  if aF2.aDen = 0 then aF2.aDen := 1;

  result.aDen := aF1.aDen*aF2.aDen;
  result.aNum := aF1.aNum*aF2.aNum;
end;

function aStrToFrac(aString: String): tFrac;
var
  iNum, iDen: Int64;
  i, i2: Integer;
begin
  result.aNum := 0;
  result.aDen := 1;
  iNum := 0;
  iDen := 0;
  for i := 1 to Length(aString) do begin
    if TryStrToInt(aString[i], i2) then begin
      Inc(iNum);
      result.aNum := result.aNum*10+i2;
    end else begin
      iDen := iNum;
    end;
  end;

  result.aDen := 1;

  if iDen > 0 then begin
    for i := 0 to (iNum-iDen-1) do result.aDen := result.aDen*10;
  end;
end;

function aFracToStr(aFrac: tFrac): String;
var
  i, iInt: Int64;
begin
  if aFrac.aDen > 0 then begin
    //Integer
    i := ((aFrac.aNum*1000) div aFrac.aDen);
    iInt := i div 1000;

    //Decimal
    i := i mod 1000;

    if i mod 10 >= 5 then i := (i div 10)+1
    else i := i div 10;
    if i >= 100 then begin
      i := i mod 100;
      Inc(iInt);
    end;

    //Result
    result := IntToStr(iInt)+',';
    if i < 10 then result := result+'0'+IntToStr(i)
    else result := result+IntToStr(i);
  end else result := 'error';
end;

procedure TMainForm.FormCreate(Sender: TObject);
var
  i: tKaM_House;
begin
  for i := Low(tKaM_House) to High(tKaM_House) do aHouseValue[i].aDen := 1;

  LabeledEdit15EditingDone(LabeledEdit15);
end;


//Unit Stats

function TMainForm.aGetIconName(aCol, aRow: Integer): String;
begin
  result := '';

  if aRow > 0 then begin
    if (StringGridStats.Cells[aCol, 0] = 'Type') AND (aRow > 2) then begin
      result := 'GroupTypes/';
      case aRow of
        3, 4, 5, 12, 15: result := result+'Melee'+IntToStr(aGroupTypesStage);
        6, 7, 14: result := result+'Ranged'+IntToStr(aGroupTypesStage);
        8, 9, 13: result := result+'Anticavalry'+IntToStr(aGroupTypesStage);
        10, 11, 16: result := result+'Cavalry'+IntToStr(aGroupTypesStage);
      end;
    end;
    if StringGridStats.Cells[aCol, 0] = '' then begin
      result := 'Portraits/';
      if aRow = 1 then begin
        result := result+'utCiv';
      end;
      if aRow > 1 then begin
        result := result+'ut'+IntToStr(aRow+11);
      end;
    end;
  end;
end;

procedure TMainForm.FormResize(Sender: TObject);
begin
  MainScrollBox.Width := MainForm.Width;
  MainScrollBox.Height := MainForm.Height;
end;

procedure TMainForm.MainTimerTimer(Sender: TObject);
var
  i: Integer;
begin
  Inc(aGroupTypesStage);
  if aGroupTypesStage > 7 then aGroupTypesStage := 0;

  for i := 0 to 15 do StringGridStatsDrawCell(StringGridStats, 11, i+1, aGroupTypesDraw[i].aRect, aGroupTypesDraw[i].aState);
end;

procedure TMainForm.StringGrid1DrawCell(Sender: TObject; aCol, aRow: Integer; aRect: TRect; aState: TGridDrawState);
var
  aIcon: TPortableNetworkGraphic;
  aFileName: String;
begin
  if (aCol = 0) AND (aRow > 0) then begin
    aFileName := 'KaM_PICS/Portraits/ut'+IntToStr(aRow+13)+'.png';

    aIcon := TPortableNetworkGraphic.Create;
    try
      aIcon.LoadFromFile(aFileName);
      StringGridRecruited.Canvas.Draw(aRect.Left+((aRect.Right-aRect.Left-aIcon.Width) div 2), aRect.Top+((aRect.Bottom-aRect.Top-aIcon.Height) div 2), aIcon);
    finally
      aIcon.Free;
    end;
  end;
end;

procedure TMainForm.StringGridStatsDrawCell(Sender: TObject; aCol, aRow: Integer; aRect: TRect; aState: TGridDrawState);
var
  aIcon: TPortableNetworkGraphic;
  aFileName: String;
begin
  aFileName := aGetIconName(aCol, aRow);
  if aFileName <> '' then begin
    aIcon := TPortableNetworkGraphic.Create;
    try
      aIcon.LoadFromFile('KaM_PICS/'+aFileName+'.png');
      StringGridStats.Canvas.Draw(aRect.Left+((aRect.Right-aRect.Left-aIcon.Width) div 2), aRect.Top+((aRect.Bottom-aRect.Top-aIcon.Height) div 2), aIcon);
      if aCol = 11 then begin
        aGroupTypesDraw[aRow-1].aRect := aRect;
        aGroupTypesDraw[aRow-1].aState := aState;
      end;
    finally
      aIcon.Free;
    end;
  end;
end;


//Production chains
function TMainForm.aSetCheckbox(aCheckBox: TCheckBox; aSender: TObject): Boolean;
begin
  if TCheckBox(aSender).Checked = True AND not (TCheckBox(aSender) = aCheckBox) then aCheckBox.Checked := False;
  result := aCheckBox.Checked;
end;

procedure TMainForm.CheckBoxEditingDone(Sender: TObject);
var
  aCheck: Boolean;
begin
  aCheck := False;

  if (Sender = CheckBox1) OR (Sender = CheckBox2) OR (Sender = CheckBox3) OR (Sender = CheckBox4) then begin
    aCheck := aSetCheckbox(CheckBox1, Sender) OR aCheck;
    aCheck := aSetCheckbox(CheckBox2, Sender) OR aCheck;
    aCheck := aSetCheckbox(CheckBox3, Sender) OR aCheck;
    aCheck := aSetCheckbox(CheckBox4, Sender) OR aCheck;

    if aCheck then begin
      Edit15.Enabled := not CheckBox4.Checked;
    end;
  end;

  if (Sender = CheckBox5) OR (Sender = CheckBox6) OR (Sender = CheckBox7) then begin
    aCheck := aSetCheckbox(CheckBox5, Sender) OR aCheck;
    aCheck := aSetCheckbox(CheckBox6, Sender) OR aCheck;
    aCheck := aSetCheckbox(CheckBox7, Sender) OR aCheck;

    if aCheck then begin
      Edit5.Enabled := not CheckBox7.Checked;
      Edit8.Enabled := not CheckBox7.Checked;
    end;
  end;

  if (Sender = CheckBox8) OR (Sender = CheckBox9) OR (Sender = CheckBox10) then begin
    aCheck := aSetCheckbox(CheckBox8, Sender) OR aCheck;
    aCheck := aSetCheckbox(CheckBox9, Sender) OR aCheck;
    aCheck := aSetCheckbox(CheckBox10, Sender) OR aCheck;

    if aCheck then begin
      Edit29.Enabled := not CheckBox10.Checked;
      Edit30.Enabled := not CheckBox10.Checked;
    end else begin
      Edit29.Enabled := False;
      Edit30.Enabled := False;
      aCheck := True;
    end;
  end;

  if (Sender = CheckBox12) OR (Sender = CheckBox13) OR (Sender = CheckBox14) then begin
    aCheck := aSetCheckbox(CheckBox12, Sender) OR aCheck;
    aCheck := aSetCheckbox(CheckBox13, Sender) OR aCheck;
    aCheck := aSetCheckbox(CheckBox14, Sender) OR aCheck;

    if aCheck then begin
      Edit2.Enabled := not CheckBox14.Checked;
    end;
  end;

  if aCheck OR (Sender = CheckBox15) then aUpdateHouses
  else TCheckBox(Sender).Checked := True;
end;

function TMainForm.aHouseToObject(aHouse: tKaM_House): TObject;
begin
  case aHouse of
    ht_ArmorSmithy: result := Edit26;
    ht_ArmorWorkshop_Armor, ht_ArmorWorkshop_Shield: result := Edit2;
    ht_Bakery: result := Edit12;
    ht_Butcher: result := Edit10;
    ht_CoalMine_Weapon, ht_CoalMine_Armor, ht_CoalMine_Gold: result := Edit33;
    ht_Farm_Horse, ht_Farm_Swine, ht_Farm_Flour: result := Edit15;
    ht_Fisher: result := Edit19;
    ht_GoldMine: result := Edit32;
    ht_IronMine_Weapon, ht_IronMine_Armor: result := Edit30;
    ht_IronSmithy_Armor, ht_IronSmithy_Weapon: result := Edit29;
    ht_Metallurgists: result := Edit31;
    ht_Mill: result := Edit13;
    ht_Quarry: result := Edit34;
    ht_Sawmill_Shield, ht_Sawmill_Weapon: result := Edit5;
    ht_School: result := Edit28;
    ht_Stables: result := Edit16;
    ht_Swine: result := Edit11;
    ht_Tannery: result := Edit4;
    ht_WeaponSmithy: result := Edit27;
    ht_WeaponWorkshop: result := Edit6;
    ht_Vineyard: result := Edit18;
    ht_Woodcutters_Shield, ht_Woodcutters_Weapon: result := Edit8;
    ht_Fish: result := Edit21;
    ht_Fish_sec: result := FishFeed;
    ht_Fish_Eat: result := Edit35;
    ht_Wine: result := Edit20;
    ht_Wine_Sec: result := WineFeed;
    ht_Wine_Eat: result := Edit36;
    ht_Horse: result := Edit17;
    ht_Loaf: result := Edit14;
    ht_Loaf_Sec: result := LoafFeed;
    ht_Loaf_Eat: result := Edit37;
    ht_Sausage: result := Edit9;
    ht_Sausage_Sec: result := SausageFeed;
    ht_Sausage_Eat: result := Edit38;
    ht_LArmor: result := Edit1;
    ht_WShield: result := Edit3;
    ht_WWeapon: result := Edit7;
    ht_IArmor: result := Edit22;
    ht_IWeapon: result := Edit23;
    ht_Unit: result := Edit24;
    ht_Stone: result := Edit25;
  end;
end;

function TMainForm.aObjectToHouse(aObj: TObject): tKaM_House;
begin
  if aObj = Edit26 then result := ht_ArmorSmithy;
  if aObj = Edit2 then begin
    if CheckBox12.Checked then result := ht_ArmorWorkshop_Armor;
    if CheckBox13.Checked then result := ht_ArmorWorkshop_Shield;
  end;
  if aObj = Edit12 then result := ht_Bakery;
  if aObj = Edit10 then result := ht_Butcher;
  if aObj = Edit15 then begin
    if CheckBox1.Checked then result := ht_Farm_Horse;
    if CheckBox2.Checked then result := ht_Farm_Flour;
    if CheckBox3.Checked then result := ht_Farm_Swine;
  end;
  if aObj = Edit19 then result := ht_Fisher;
  if aObj = Edit32 then result := ht_GoldMine;
  if aObj = Edit30 then begin
    if CheckBox8.Checked then result := ht_IronMine_Armor;
    if CheckBox9.Checked then result := ht_IronMine_Weapon;
  end;
  if aObj = Edit29 then begin
    if CheckBox8.Checked then result := ht_IronSmithy_Armor;
    if CheckBox9.Checked then result := ht_IronSmithy_Weapon;
  end;
  if aObj = Edit31 then result := ht_Metallurgists;
  if aObj = Edit13 then result := ht_Mill;
  if aObj = Edit34 then result := ht_Quarry;
  if aObj = Edit5 then begin
    if CheckBox5.Checked then result := ht_Sawmill_Shield;
    if CheckBox6.Checked then result := ht_Sawmill_Weapon;
  end;
  if aObj = Edit28 then result := ht_School;
  if aObj = Edit16 then result := ht_Stables;
  if aObj = Edit11 then result := ht_Swine;
  if aObj = Edit4 then result := ht_Tannery;
  if aObj = Edit27 then result := ht_WeaponSmithy;
  if aObj = Edit6 then result := ht_WeaponWorkshop;
  if aObj = Edit18 then result := ht_Vineyard;
  if aObj = Edit8 then begin
    if CheckBox5.Checked then result := ht_Woodcutters_Shield;
    if CheckBox6.Checked then result := ht_Woodcutters_Weapon;
  end;
  if aObj = Edit21 then result := ht_Fish;
  if aObj = Edit35 then result := ht_Fish_Eat;
  if aObj = Edit20 then result := ht_Wine;
  if aObj = Edit36 then result := ht_Wine_Eat;
  if aObj = Edit17 then result := ht_Horse;
  if aObj = Edit14 then result := ht_Loaf;
  if aObj = Edit37 then result := ht_Loaf_Eat;
  if aObj = Edit9 then result := ht_Sausage;
  if aObj = Edit38 then result := ht_Sausage_Eat;
  if aObj = Edit1 then result := ht_LArmor;
  if aObj = Edit3 then result := ht_WShield;
  if aObj = Edit7 then result := ht_WWeapon;
  if aObj = Edit22 then result := ht_IArmor;
  if aObj = Edit23 then result := ht_IWeapon;
  if aObj = Edit24 then result := ht_Unit;
  if aObj = Edit25 then result := ht_Stone;
end;

function TMainForm.aGetValue(aDir: tDirection; aHouse: tKaM_House): tFrac;
begin
  //Values collected with a 180-minutes-long-full-production test, simplified where possible
  //These values are the number of aHouse that are appropriate for 1 of its raw gatherer
  case aHouse of
    ht_ArmorSmithy: result := aGetFrac(42731, 41640); //346*247, 240*347
    ht_ArmorWorkshop_Armor: result := aGetFrac(9362304, 24202739); //504*86*216, 271*253*353
    ht_ArmorWorkshop_Shield: result := aGetFrac(46354, 40921); //602*154, 271*302
    ht_Bakery: result := aGetFrac(54432, 67045); //252*216, 265*253
    ht_Butcher: result := aGetFrac(344, 1765); //86*216, 270*353
    ht_IronSmithy_Armor, ht_IronSmithy_Weapon: result := aGetFrac(247, 347);
    ht_Metallurgists: result := aGetFrac(247, 262);
    ht_Mill: result := aGetFrac(216, 253);
    ht_Sawmill_Shield, ht_Sawmill_Weapon: result := aGetFrac(77, 151); //154, 302
    ht_School: result := aGetFrac(741, 1048); //522*247, 696*262
    ht_Stables: result := aGetFrac(216, 443);
    ht_Swine: result := aGetFrac(216, 353);
    ht_Tannery: result := aGetFrac(18576, 89309); //86*216, 253*353
    ht_WeaponSmithy: result := aGetFrac(42731, 51703); //346*247, 298*347
    ht_WeaponWorkshop: result := aGetFrac(23177, 46810); //602*154, 620*302

    ht_Fish: result := aGetFrac(103, 90); //206, 180
    ht_Fish_Sec: result := aGetFrac(1545, 1); //13500*206, 10*180
    ht_Fish_Eat: result := aGetFrac(103, 4); //1*13500*206, 60*10*180
    ht_Wine: result := aGetFrac(31, 30); //186, 180
    ht_Wine_Sec: result := aGetFrac(837, 1); //8100*186, 10*180
    ht_Wine_Eat: result := aGetFrac(279, 20); //1*8100*186, 60*10*180
    ht_Horse: result := aGetFrac(654, 2215); //109*216, 180*443
    ht_Loaf: result := aGetFrac(72576, 30475); //528*252*216, 180*265*253
    ht_Loaf_Sec: result := aGetFrac(15676416, 6095); //10800*528*252*216, 10*180*265*253
    ht_Loaf_Eat: result := aGetFrac(1306368, 30475); //1*10800*528*252*216, 60*10*180*265*253
    ht_Sausage: result := aGetFrac(1548, 1765); //810*86*216, 180*270*353
    ht_Sausage_Sec: result := aGetFrac(501552, 353); //16200*810*86*216, 10*180*270*353
    ht_Sausage_Eat: result := aGetFrac(41796, 1765); //1*16200*810*86*216, 60*10*180*270*353
    ht_LArmor: result := aGetFrac(14043456, 24202739); //270*504*86*216, 180*271*253*353
    ht_WShield: result := aGetFrac(69531, 40921); //270*602*154, 180*271*302
    ht_WWeapon: result := aGetFrac(2387231, 2808600); //309*602*154, 180*620*302
    ht_IArmor: result := aGetFrac(42731, 31230); //240*346*247, 180*240*347
    ht_IWeapon: result := aGetFrac(1410123, 1034060); //297*346*247, 180*298*347
    ht_Unit: result := aGetFrac(7163, 2620); //696*522*247, 180*696*262
    ht_Stone: result := aGetFrac(24, 5); //864, 180

    //Coal Mine is not editable, and it is treated as if it wasn't a raw gatherer
    ht_CoalMine_Weapon: result := aGetFrac(1965645, 1899478); //247*346*298+247*347, 347*298*238+347*238
    ht_CoalMine_Armor: result := aGetFrac(20596589, 19903226); //247*346*240+247*347, 347*240*238+347*238
    ht_CoalMine_Gold: result := aGetFrac(247, 238); //247*262, 262*238
  end;

  if aDir = tToRaw then result := aGetFrac(result.aDen, result.aNum);
end;

function TMainForm.aGetHouses(aDir: tDirection; aHouse: tKaM_House): tKaM_House_Array;
begin
  if aDir = tFromRaw then begin
    if aHouse = ht_Fisher then begin
      SetLength(result, 3);
      result[0] := ht_Fish;
      result[1] := ht_Fish_Sec;
      result[2] := ht_Fish_Eat;
    end;

    if aHouse = ht_Vineyard then begin
      SetLength(result, 3);
      result[0] := ht_Wine;
      result[1] := ht_Wine_Sec;
      result[2] := ht_Wine_Eat;
    end;

    if aHouse = ht_Farm_Horse then begin
      SetLength(result, 2);
      result[0] := ht_Stables;
      result[1] := ht_Horse;
    end;
    if aHouse = ht_Farm_Swine then begin
      SetLength(result, 8);
      result[0] := ht_Swine;
      result[1] := ht_Tannery;
      result[2] := ht_ArmorWorkshop_Armor;
      result[3] := ht_LArmor;
      result[4] := ht_Butcher;
      result[5] := ht_Sausage;
      result[6] := ht_Sausage_Sec;
      result[7] := ht_Sausage_Eat;
    end;
    if aHouse = ht_Farm_Flour then begin
      SetLength(result, 5);
      result[0] := ht_Mill;
      result[1] := ht_Bakery;
      result[2] := ht_Loaf;
      result[3] := ht_Loaf_Sec;
      result[4] := ht_Loaf_Eat;
    end;

    if aHouse = ht_Woodcutters_Shield then begin
      SetLength(result, 3);
      result[0] := ht_Sawmill_Shield;
      result[1] := ht_ArmorWorkshop_Shield;
      result[2] := ht_WShield;
    end;
    if aHouse = ht_Woodcutters_Weapon then begin
      SetLength(result, 3);
      result[0] := ht_Sawmill_Weapon;
      result[1] := ht_WeaponWorkshop;
      result[2] := ht_WWeapon;
    end;

    if aHouse = ht_IronMine_Armor then begin
      SetLength(result, 4);
      result[0] := ht_IronSmithy_Armor;
      result[1] := ht_ArmorSmithy;
      result[2] := ht_IArmor;
      result[3] := ht_CoalMine_Armor;
    end;
    if aHouse = ht_IronMine_Weapon then begin
      SetLength(result, 4);
      result[0] := ht_IronSmithy_Weapon;
      result[1] := ht_WeaponSmithy;
      result[2] := ht_IWeapon;
      result[3] := ht_CoalMine_Weapon;
    end;

    if aHouse = ht_GoldMine then begin
      SetLength(result, 4);
      result[0] := ht_Metallurgists;
      result[1] := ht_School;
      result[2] := ht_Unit;
      result[3] := ht_CoalMine_Gold;
    end;

    if aHouse = ht_Quarry then begin
      SetLength(result, 1);
      result[0] := ht_Stone;
    end;
  end else begin
    SetLength(result, 1);

    case aHouse of
      ht_IArmor, ht_ArmorSmithy, ht_IronSmithy_Armor: result[0] := ht_IronMine_Armor;
      ht_IWeapon, ht_WeaponSmithy, ht_IronSmithy_Weapon: result[0] := ht_IronMine_Weapon;

      ht_Unit, ht_School, ht_Metallurgists: result[0] := ht_GoldMine;

      ht_Loaf, ht_Loaf_Eat, ht_Bakery, ht_Mill: result[0] := ht_Farm_Flour;
      ht_Horse, ht_Stables: result[0] := ht_Farm_Horse;
      ht_LArmor, ht_ArmorWorkshop_Armor, ht_Tannery, ht_Sausage, ht_Sausage_Eat, ht_Butcher, ht_Swine: result[0] := ht_Farm_Swine;

      ht_WShield, ht_ArmorWorkshop_Shield, ht_Sawmill_Shield: result[0] := ht_Woodcutters_Shield;
      ht_WWeapon, ht_WeaponWorkshop, ht_Sawmill_Weapon: result[0] := ht_Woodcutters_Weapon;


      ht_Fish, ht_Fish_Eat: result[0] := ht_Fisher;

      ht_Wine, ht_Wine_Eat: result[0] := ht_Vineyard;

      ht_Stone: result[0] := ht_Quarry;
    end;
  end;
end;

procedure TMainForm.aUpdateHouses;
begin
  if CheckBox1.Checked then Edit15.Text := aFracToStr(aHouseValue[ht_Farm_Horse]);
  if CheckBox2.Checked then Edit15.Text := aFracToStr(aHouseValue[ht_Farm_Flour]);
  if CheckBox3.Checked then Edit15.Text := aFracToStr(aHouseValue[ht_Farm_Swine]);
  if CheckBox4.Checked then Edit15.Text := aFracToStr( aAddFracs(aHouseValue[ht_Farm_Horse], aAddFracs(aHouseValue[ht_Farm_Flour], aHouseValue[ht_Farm_Swine]) ) );

  if CheckBox5.Checked then begin
    Edit5.Text := aFracToStr(aHouseValue[ht_Sawmill_Shield]);
    Edit8.Text := aFracToStr(aHouseValue[ht_Woodcutters_Shield]);
  end;
  if CheckBox6.Checked then begin
    Edit5.Text := aFracToStr(aHouseValue[ht_Sawmill_Weapon]);
    Edit8.Text := aFracToStr(aHouseValue[ht_Woodcutters_Weapon]);
  end;
  if CheckBox7.Checked then begin
    Edit5.Text := aFracToStr(aAddFracs(aHouseValue[ht_Sawmill_Shield], aHouseValue[ht_Sawmill_Weapon]));
    Edit8.Text := aFracToStr(aAddFracs(aHouseValue[ht_Woodcutters_Shield], aHouseValue[ht_Woodcutters_Weapon]));
  end;

  if CheckBox8.Checked then begin
    Edit29.Text := aFracToStr(aHouseValue[ht_IronSmithy_Armor]);
    Edit30.Text := aFracToStr(aHouseValue[ht_IronMine_Armor]);

    if CheckBox15.Checked then Edit33.Text := aFracToStr(aAddFracs(aHouseValue[ht_CoalMine_Gold], aHouseValue[ht_CoalMine_Armor]))
    else Edit33.Text := aFracToStr(aHouseValue[ht_CoalMine_Armor]);
  end;
  if CheckBox9.Checked then begin
    Edit29.Text := aFracToStr(aHouseValue[ht_IronSmithy_Weapon]);
    Edit30.Text := aFracToStr(aHouseValue[ht_IronMine_Weapon]);

    if CheckBox15.Checked then Edit33.Text := aFracToStr(aAddFracs(aHouseValue[ht_CoalMine_Gold], aHouseValue[ht_CoalMine_Weapon]))
    else Edit33.Text := aFracToStr(aHouseValue[ht_CoalMine_Weapon]);
  end;
  if CheckBox10.Checked then begin
    Edit29.Text := aFracToStr(aAddFracs(aHouseValue[ht_IronSmithy_Armor], aHouseValue[ht_IronSmithy_Weapon]));
    Edit30.Text := aFracToStr(aAddFracs(aHouseValue[ht_IronMine_Armor], aHouseValue[ht_IronMine_Weapon]));

    if CheckBox15.Checked then Edit33.Text := aFracToStr(aAddFracs(aHouseValue[ht_CoalMine_Gold], aAddFracs(aHouseValue[ht_CoalMine_Weapon], aHouseValue[ht_CoalMine_Armor])))
    else Edit33.Text := aFracToStr(aAddFracs(aHouseValue[ht_CoalMine_Weapon], aHouseValue[ht_CoalMine_Armor]));
  end;
  if not (CheckBox8.Checked OR CheckBox9.Checked OR CheckBox10.Checked) then begin
    Edit29.Text := aFracToStr(aGetFrac(0, 1));
    Edit30.Text := aFracToStr(aGetFrac(0, 1));

    if CheckBox15.Checked then Edit33.Text := aFracToStr(aHouseValue[ht_CoalMine_Gold])
    else Edit33.Text := aFracToStr(aGetFrac(0, 1));
  end;

  if CheckBox12.Checked then Edit2.Text := aFracToStr(aHouseValue[ht_ArmorWorkshop_Armor]);
  if CheckBox13.Checked then Edit2.Text := aFracToStr(aHouseValue[ht_ArmorWorkshop_Shield]);
  if CheckBox14.Checked then Edit2.Text := aFracToStr(aAddFracs(aHouseValue[ht_ArmorWorkshop_Armor], aHouseValue[ht_ArmorWorkshop_Shield]));
end;

procedure TMainForm.EditRawDo(aHouse: tKaM_House);
var
  iHouses: tKaM_House_Array;
  i: Integer;
  iFrac: tFrac;
begin
  iHouses := aGetHouses(tFromRaw, aHouse);
  for i := 0 to Length(iHouses)-1 do begin
    aHouseValue[iHouses[i]] := aSimplify(aMultFracs(aGetValue(tFromRaw, iHouses[i]), aHouseValue[aHouse]));

    if iHouses[i] in [ht_Fish_Sec, ht_Wine_Sec, ht_Loaf_Sec, ht_Sausage_Sec] then TStaticText(aHouseToObject(iHouses[i])).Caption := '('+aFracToStr(aHouseValue[iHouses[i]])+' s)'
    else TEdit(aHouseToObject(iHouses[i])).Text := aFracToStr(aHouseValue[iHouses[i]]);
  end;

  aUpdateHouses;
end;

procedure TMainForm.EditWare(Sender: TObject);
var
  iHouses: tKaM_House_Array;
begin
  if not aIsSameFrac(aHouseValue[aObjectToHouse(Sender)], aStrToFrac(TEdit(Sender).Text)) then begin
    aHouseValue[aObjectToHouse(Sender)] := aStrToFrac(TEdit(Sender).Text);

    iHouses := aGetHouses(tToRaw, aObjectToHouse(Sender));
    aHouseValue[iHouses[0]] := aSimplify(aMultFracs(aGetValue(tToRaw, aObjectToHouse(Sender)), aHouseValue[aObjectToHouse(Sender)]));
    TEdit(aHouseToObject(iHouses[0])).Text := aFracToStr(aHouseValue[iHouses[0]]);

    EditRawDo(iHouses[0]);
  end;
end;

procedure TMainForm.EditRaw(Sender: TObject);
begin
  aHouseValue[aObjectToHouse(Sender)] := aStrToFrac(TEdit(Sender).Text);

  EditRawDo(aObjectToHouse(Sender));
end;


//Fighting

procedure TMainForm.ComboBox1EditingDone(Sender: TObject);
var
  iChance, iDefence: tFrac;
  iAttack, iDirMod: Integer;
  iString: String;
begin
  ComboBox3.Enabled := not ((ComboBox1.ItemIndex = 3) OR (ComboBox1.ItemIndex = 4) OR (ComboBox1.ItemIndex = 11));

  iAttack := StrToInt(StringGridStats.Cells[3, ComboBox1.ItemIndex+3]);
  if (ComboBox2.ItemIndex = 8) OR (ComboBox2.ItemIndex = 9) OR (ComboBox2.ItemIndex = 14) then
    if (ComboBox1.ItemIndex = 5) OR (ComboBox1.ItemIndex = 6) OR (ComboBox1.ItemIndex = 10) then begin
      iString := StringGridStats.Cells[4, ComboBox1.ItemIndex+3];
      Delete(iString, 1, 1);
      iAttack := iAttack+StrToInt(iString);
    end;

  iDefence.aNum := StrToInt(StringGridStats.Cells[6, ComboBox2.ItemIndex+2]);
  iDefence.aDen := 1;
  if (ComboBox2.ItemIndex = 2) OR (ComboBox2.ItemIndex = 3) OR (ComboBox2.ItemIndex = 8) OR (ComboBox2.ItemIndex = 9) then begin
    if (ComboBox1.ItemIndex = 3) OR (ComboBox1.ItemIndex = 11) then Inc(iDefence.aNum);
    if ComboBox1.ItemIndex = 4 then begin
      iDefence.aNum := (iDefence.aNum)*100+25;
      iDefence.aDen := 100;
    end;
  end;

  if ComboBox3.Enabled then iDirMod := ComboBox3.ItemIndex+1
  else iDirMod := 1;

  iChance.aNum := iAttack*iDirMod*iDefence.aDen;
  iChance.aDen := iDefence.aNum;

  Label21.Caption := IntToStr(iAttack)+' x '+IntToStr(iDirMod);
  if iDefence.aDen = 1 then Label22.Caption := IntToStr(iDefence.aNum)
  else Label22.Caption := aFracToStr(iDefence);

  Label20.Caption := aFracToStr(aSimplify(iChance))+'%  =';

  //Now the layout
  Shape2.Width := Label21.Width+35;
  Label20.Left := Shape2.Left-Label20.Width-12;
  Label21.Left := Shape2.Left+(Shape2.Width div 2)-(Label21.Width div 2);
  Label22.Left := Shape2.Left+(Shape2.Width div 2)-(Label22.Width div 2);
end;


//Unit Counters

procedure TMainForm.ComboBox5Change(Sender: TObject);
begin
  if TComboBox(Sender).ItemIndex > 0 then begin
    if Sender = ComboBox5 then ComboBox6.ItemIndex := 0;
    if Sender = ComboBox6 then ComboBox5.ItemIndex := 0;
  end;

  aUpdateScheme;
end;

procedure TMainForm.LabeledEdit15EditingDone(Sender: TObject);
var
  iFrac: tFrac;
begin
  iFrac := aStrToFrac(LabeledEdit15.Text);
  aStartTime := Round(60*((iFrac.aNum/iFrac.aDen)-10));

  iFrac := aStrToFrac(LabeledEdit16.Text);
  aTotalTime := Round(60*((iFrac.aNum/iFrac.aDen)-10));

  if aStartTime < 0 then aStartTime := 0;
  if aTotalTime < 0 then aTotalTime := 0;
  if aStartTime > aTotalTime then aStartTime := aTotalTime;

  ComboBox4Change(ComboBox4); //Also updates the scheme
end;

function aOtherPlayer(aPlayer: tPlayerType): tPlayerType;
begin
  if aPlayer = tPlayer then result := tEnemy
  else result := tPlayer;
end;

function aGetNumRatio(aWarrior1, aWarrior2: tKaM_Warrior): tFrac;
var
  iUnit, iUnit2: tKaM_Warrior;
  aReversed: Boolean;
  i: Integer;
begin
  if aWarrior1 = aWarrior2 then begin
    result.aNum := 1;
    result.aDen := 1;
    Exit;
  end;

  if aWarrior1 < aWarrior2 then begin
    iUnit := aWarrior1;
    iUnit2 := aWarrior2;
    aReversed := False;
  end else begin
    iUnit := aWarrior2;
    iUnit2 := aWarrior1;
    aReversed := True;
  end;

  if iUnit = ut_Militia then case iUnit2 of
    ut_AxeFighter: begin
      result.aNum := 12;
      result.aDen := 7;
    end;
    ut_SwordFighter: begin
      result.aNum := 18;
      result.aDen := 6;
    end;
    ut_Bowman: begin
      result.aNum := 12;
      result.aDen := 13;
    end;
    ut_Crossbowman: begin
      result.aNum := 10;
      result.aDen := 10;
    end;
    ut_LanceCarrier: begin
      result.aNum := 6;
      result.aDen := 5;
    end;
    ut_Pikeman: begin
      result.aNum := 14;
      result.aDen := 6;
    end;
    ut_Scout: begin
      result.aNum := 14;
      result.aDen := 6;
    end;
    ut_Knight: begin
      result.aNum := 24;
      result.aDen := 6;
    end;
  end;

  if iUnit = ut_AxeFighter then case iUnit2 of
    ut_SwordFighter: begin
      result.aNum := 19;
      result.aDen := 9;
    end;
    ut_Bowman: begin
      result.aNum := 6;
      result.aDen := 12;
    end;
    ut_Crossbowman: begin
      result.aNum := 9;
      result.aDen := 13;
    end;
    ut_LanceCarrier: begin
      result.aNum := 6;
      result.aDen := 8;
    end;
    ut_Pikeman: begin
      result.aNum := 5;
      result.aDen := 4;
    end;
    ut_Scout: begin
      result.aNum := 10;
      result.aDen := 8;
    end;
    ut_Knight: begin
      result.aNum := 14;
      result.aDen := 7;
    end;
  end;

  if iUnit = ut_SwordFighter then case iUnit2 of
    ut_Bowman: begin
      result.aNum := 4;
      result.aDen := 11;
    end;
    ut_Crossbowman: begin
      result.aNum := 6;
      result.aDen := 12;
    end;
    ut_LanceCarrier: begin
      result.aNum := 8;
      result.aDen := 16;
    end;
    ut_Pikeman: begin
      result.aNum := 7;
      result.aDen := 9;
    end;
    ut_Scout: begin
      result.aNum := 4;
      result.aDen := 5;
    end;
    ut_Knight: begin
      result.aNum := 10;
      result.aDen := 8;
    end;
  end;

  if iUnit = ut_Bowman then case iUnit2 of
    ut_Crossbowman: begin
      result.aNum := 4;
      result.aDen := 3;
    end;
    ut_LanceCarrier: begin
      result.aNum := 12;
      result.aDen := 9;
    end;
    ut_Pikeman: begin
      result.aNum := 13;
      result.aDen := 7;
    end;
    ut_Scout: begin
      result.aNum := 10;
      result.aDen := 3;
    end;
    ut_Knight: begin
      result.aNum := 13;
      result.aDen := 3;
    end;
  end;

  if iUnit = ut_Crossbowman then case iUnit2 of
    ut_LanceCarrier: begin
      result.aNum := 10;
      result.aDen := 9;
    end;
    ut_Pikeman: begin
      result.aNum := 15;
      result.aDen := 9;
    end;
    ut_Scout: begin
      result.aNum := 10;
      result.aDen := 5;
    end;
    ut_Knight: begin
      result.aNum := 21;
      result.aDen := 7;
    end;
  end;

  if iUnit = ut_LanceCarrier then case iUnit2 of
    ut_Pikeman: begin
      result.aNum := 3;
      result.aDen := 2;
    end;
    ut_Scout: begin
      result.aNum := 4;
      result.aDen := 5;
    end;
    ut_Knight: begin
      result.aNum := 16;
      result.aDen := 12;
    end;
  end;

  if iUnit = ut_Pikeman then case iUnit2 of
    ut_Scout: begin
      result.aNum := 4;
      result.aDen := 7;
    end;
    ut_Knight: begin
      result.aNum := 11;
      result.aDen := 13;
    end;
  end;

  if iUnit = ut_Scout then begin
    result.aNum := 14;
    result.aDen := 9;
  end;

  if aReversed then begin
    i := result.aNum;
    result.aNum := result.aDen;
    result.aDen := i;
  end;
end;

function aRequiredMines(aWarrior: tKaM_Warrior; aMine: tResources): tFrac;
begin
  if aMine = tGold then result := aGetFrac(14143, 10000);

  if aMine = tCoal then begin
    case aWarrior of
      ut_SwordFighter, ut_Knight: result := aGetFrac(190591, 10000);
      ut_Crossbowman, ut_Pikeman: result := aGetFrac(132019, 10000);
      else result := aGetFrac(14678, 10000);
    end;
  end;

  if aMine = tIron then begin
    case aWarrior of
      ut_SwordFighter, ut_Knight: result := aGetFrac(84874, 10000);
      ut_Crossbowman, ut_Pikeman: result := aGetFrac(56614, 10000);
      else result := aGetFrac(0, 0);
    end;
  end;
end;

function aGetJBuildTime(aWarrior: tKaM_Warrior; aPlayer: tPlayerType; aOrder: tOrder): tBuildTimes;
var
  aBaseTime, aDimension, aDistTot, aDistNum, aWares: tBuildTimes; //Sqrt(Dimensions), distances, numbers and wares are x10000
  iMine, iMineD, iMineDist, iMineN, iMineW: array[tGold..tCoal] of tBuildTimes;
  i: Integer;
begin
  iMine[tGold][0] := 145;
  iMine[tCoal][0] := 200;
  iMine[tIron][0] := 161;

  iMine[tGold][3] := 1287;
  iMine[tCoal][3] := 1861;
  iMine[tIron][3] := 1931;

  iMineD[tGold][0] := 50000;
  iMineD[tCoal][0] := 120000;
  iMineD[tIron][0] := 70000;

  iMineD[tGold][3] := 114352;
  iMineD[tCoal][3] := 396667;
  iMineD[tIron][3] := 240139;

  iMineDist[tGold][0] := Round(aLocs[aPlayer].aDistance[tGold].aNum*10000/aLocs[aPlayer].aDistance[tGold].aDen);
  iMineDist[tCoal][0] := Round(aLocs[aPlayer].aDistance[tCoal].aNum*10000/aLocs[aPlayer].aDistance[tCoal].aDen);
  iMineDist[tIron][0] := Round(aLocs[aPlayer].aDistance[tIron].aNum*10000/aLocs[aPlayer].aDistance[tIron].aDen);

  iMineDist[tGold][3] := Round(aLocs[aPlayer].aDistance[tFertile].aNum*22870/aLocs[aPlayer].aDistance[tFertile].aDen);
  iMineDist[tCoal][3] := Round(aLocs[aPlayer].aDistance[tFertile].aNum*33056/aLocs[aPlayer].aDistance[tFertile].aDen);
  iMineDist[tIron][3] := Round(aLocs[aPlayer].aDistance[tFertile].aNum*34306/aLocs[aPlayer].aDistance[tFertile].aDen);

  iMineN[tGold][0] := 10000;
  iMineN[tCoal][0] := 10000;
  iMineN[tIron][0] := 10000;

  iMineN[tGold][3] := 22870;
  iMineN[tCoal][3] := 33056;
  iMineN[tIron][3] := 34306;

  iMineW[tGold][0] := 80000;
  iMineW[tCoal][0] := 110000;
  iMineW[tIron][0] := 90000;

  iMineW[tGold][3] := 526019;
  iMineW[tCoal][3] := 760278;
  iMineW[tIron][3] := 789028;

  for i := 1 to 3 do begin
    if aOrder[i-1] = tGold then begin
      iMine[tGold][i] := iMine[tGold][3];
      iMineD[tGold][i] := iMineD[tGold][3];
      iMineDist[tGold][i] := iMineDist[tGold][3];
      iMineN[tGold][i] := iMineN[tGold][3];
      iMineW[tGold][i] := iMineW[tGold][3];
    end else begin
      iMine[tGold][i] := iMine[tGold][i-1];
      iMineD[tGold][i] := iMineD[tGold][i-1];
      iMineDist[tGold][i] := iMineDist[tGold][i-1];
      iMineN[tGold][i] := iMineN[tGold][i-1];
      iMineW[tGold][i] := iMineW[tGold][i-1];
    end;

    if aOrder[i-1] = tCoal then begin
      iMine[tCoal][i] := iMine[tCoal][3];
      iMineD[tCoal][i] := iMineD[tCoal][3];
      iMineDist[tCoal][i] := iMineDist[tCoal][3];
      iMineN[tCoal][i] := iMineN[tCoal][3];
      iMineW[tCoal][i] := iMineW[tCoal][3];
    end else begin
      iMine[tCoal][i] := iMine[tCoal][i-1];
      iMineD[tCoal][i] := iMineD[tCoal][i-1];
      iMineDist[tCoal][i] := iMineDist[tCoal][i-1];
      iMineN[tCoal][i] := iMineN[tCoal][i-1];
      iMineW[tCoal][i] := iMineW[tCoal][i-1];
    end;

    if aOrder[i-1] = tIron then begin
      iMine[tIron][i] := iMine[tIron][3];
      iMineD[tIron][i] := iMineD[tIron][3];
      iMineDist[tIron][i] := iMineDist[tIron][3];
      iMineN[tIron][i] := iMineN[tIron][3];
      iMineW[tIron][i] := iMineW[tIron][3];
    end else begin
      iMine[tIron][i] := iMine[tIron][i-1];
      iMineD[tIron][i] := iMineD[tIron][i-1];
      iMineDist[tIron][i] := iMineDist[tIron][i-1];
      iMineN[tIron][i] := iMineN[tIron][i-1];
      iMineW[tIron][i] := iMineW[tIron][i-1];
    end;
  end;

  for i := 0 to 3 do begin //Recruit
    aBaseTime[i] := Round(710.1687+1.4143*iMine[tGold][i]+1.4678*iMine[tCoal][i]);
    aDimension[i] := Round(3733333333+1.4143*iMineD[tGold][i]+1.4678*iMineD[tCoal][i]);
    aDistTot[i] := Round(23333+1.4143*iMineDist[tGold][i]+1.4678*iMineDist[tCoal][i]);
    aDistNum[i] := Round(23333+1.4143*iMineN[tGold][i]+1.4678*iMineN[tCoal][i]);
    aWares[i] := Round(366667+1.4143*iMineW[tGold][i]+1.4678*iMineW[tCoal][i]);
  end;

  if aWarrior in [ut_AxeFighter, ut_Bowman, ut_LanceCarrier, ut_Scout] then begin //Leather Armor
    for i := 0 to 3 do begin
      aBaseTime[i] := aBaseTime[i]+6629;
      aDimension[i] := aDimension[i]+38549195872;
      aDistTot[i] := aDistTot[i]+Round(93403+66639*aLocs[aPlayer].aDistance[tFertile].aNum/aLocs[aPlayer].aDistance[tFertile].aDen);
      aDistNum[i] := aDistNum[i]+160041;
      aWares[i] := aWares[i]+3193453;
    end;
  end else begin //Loaf
    for i := 0 to 3 do begin
      aBaseTime[i] := aBaseTime[i]+4123;
      aDimension[i] := aDimension[i]+21437773782;
      aDistTot[i] := aDistTot[i]+Round(61316+36813*aLocs[aPlayer].aDistance[tFertile].aNum/aLocs[aPlayer].aDistance[tFertile].aDen);
      aDistNum[i] := aDistNum[i]+98128;
      aWares[i] := aWares[i]+1673682;
    end;
  end;

  if aWarrior in [ut_SwordFighter, ut_Crossbowman, ut_Pikeman, ut_Knight] then begin
    for i := 0 to 3 do begin //Iron Armor
      aBaseTime[i] := aBaseTime[i]+Round(1595.3145+2.8260*iMine[tIron][i]+5.8572*iMine[tCoal][i]);
      aDimension[i] := aDimension[i]+Round(8237341040+2.8260*iMineD[tIron][i]+5.8572*iMineD[tCoal][i]);
      aDistTot[i] := aDistTot[i]+Round(49116+2.8260*iMineDist[tIron][i]+5.8572*iMineDist[tCoal][i]);
      aDistNum[i] := aDistNum[i]+Round(49116+2.8260*iMineN[tIron][i]+5.8572*iMineN[tCoal][i]);
      aWares[i] := aWares[i]+Round(948619+2.8260*iMineW[tIron][i]+5.8572*iMineW[tCoal][i]);
    end;
    for i := 0 to 3 do begin //Iron Weapon
      aBaseTime[i] := aBaseTime[i]+Round(1148.4448+2.8355*iMine[tIron][i]+5.8769*iMine[tCoal][i]);
      aDimension[i] := aDimension[i]+Round(6542651953+2.8355*iMineD[tIron][i]+5.8769*iMineD[tCoal][i]);
      aDistTot[i] := aDistTot[i]+Round(43618+2.8355*iMineDist[tIron][i]+5.8769*iMineDist[tCoal][i]);
      aDistNum[i] := aDistNum[i]+Round(43618+2.8355*iMineN[tIron][i]+5.8769*iMineN[tCoal][i]);
      aWares[i] := aWares[i]+Round(610648+2.8355*iMineW[tIron][i]+5.8769*iMineW[tCoal][i]);
    end;
  end else begin //Wooden Weapon
    for i := 0 to 3 do begin
      aBaseTime[i] := aBaseTime[i]+2114;
      aDimension[i] := aDimension[i]+43706582229;
      aDistTot[i] := aDistTot[i]+Round(45722+45492*aLocs[aPlayer].aDistance[tFertile].aNum/aLocs[aPlayer].aDistance[tFertile].aDen);
      aDistNum[i] := aDistNum[i]+91214;
      aWares[i] := aWares[i]+1140517;
    end;
  end;

  if aWarrior in [ut_SwordFighter, ut_Knight] then begin //Iron Shield
    for i := 0 to 3 do begin
      aBaseTime[i] := aBaseTime[i]+Round(1595.3145+2.8260*iMine[tIron][i]+5.8572*iMine[tCoal][i]);
      aDimension[i] := aDimension[i]+Round(8237341040+2.8260*iMineD[tIron][i]+5.8572*iMineD[tCoal][i]);
      aDistTot[i] := aDistTot[i]+Round(49116+2.8260*iMineDist[tIron][i]+5.8572*iMineDist[tCoal][i]);
      aDistNum[i] := aDistNum[i]+Round(49116+2.8260*iMineN[tIron][i]+5.8572*iMineN[tCoal][i]);
      aWares[i] := aWares[i]+Round(948619+2.8260*iMineW[tIron][i]+5.8572*iMineW[tCoal][i]);
    end;
  end;

  if aWarrior in [ut_AxeFighter, ut_Scout] then begin //Wooden Shield
    for i := 0 to 3 do begin
      aBaseTime[i] := aBaseTime[i]+1439;
      aDimension[i] := aDimension[i]+24040032791;
      aDistTot[i] := aDistTot[i]+Round(37382+22756*aLocs[aPlayer].aDistance[tFertile].aNum/aLocs[aPlayer].aDistance[tFertile].aDen);
      aDistNum[i] := aDistNum[i]+60139;
      aWares[i] := aWares[i]+773670;
    end;
  end;

  if aWarrior in [ut_Scout, ut_Knight] then begin
    for i := 0 to 3 do begin //Horse
      aBaseTime[i] := aBaseTime[i]+10316;
      aDimension[i] := aDimension[i]+58606014271;
      aDistTot[i] := aDistTot[i]+Round(63853+130958*aLocs[aPlayer].aDistance[tFertile].aNum/aLocs[aPlayer].aDistance[tFertile].aDen);
      aDistNum[i] := aDistNum[i]+194811;
      aWares[i] := aWares[i]+4736075;
    end;
  end;

  for i := 0 to 3 do aWares[i] := Round(aWares[i]/20); //The contribution of the number of serfs
  for i := 0 to 3 do aBaseTime[i] := Round(aBaseTime[i]/7.5); //The contribution of the number of laborers

  for i := 0 to 3 do result[i] := Round(aBaseTime[i]+(((Sqrt(aDimension[i])/10000)+(aDistTot[i]/aDistNum[i]))*aWares[i]/(aDistNum[i]*0.988)));//Dimensions, distances, numbers and wares are x10000
end;

procedure aUpdateRecruited(aWarrior: tKaM_Warrior; aPlayer: tPlayerType);
var
  aNumChainsToFill: array[tGold..tCoal] of tFrac;
  aOrder: tOrder; //0 lowest, 2 highest
  iFrac: tFrac;
  iJBuildTime: tBuildTimes;
  i: Integer;
begin
  iFrac := aRequiredMines(aWarrior, tGold);
  aNumChainsToFill[tGold] := aGetFrac(aLocs[aPlayer].aMaxMines[tGold].aNum*iFrac.aDen, aLocs[aPlayer].aMaxMines[tGold].aDen*iFrac.aNum);

  iFrac := aRequiredMines(aWarrior, tIron);
  aNumChainsToFill[tIron] := aGetFrac(aLocs[aPlayer].aMaxMines[tIron].aNum*iFrac.aDen, aLocs[aPlayer].aMaxMines[tIron].aDen*iFrac.aNum);

  iFrac := aRequiredMines(aWarrior, tCoal);
  aNumChainsToFill[tCoal] := aGetFrac(aLocs[aPlayer].aMaxMines[tCoal].aNum*iFrac.aDen, aLocs[aPlayer].aMaxMines[tCoal].aDen*iFrac.aNum);

  if (aNumChainsToFill[tGold].aNum*aNumChainsToFill[tCoal].aDen) > (aNumChainsToFill[tCoal].aNum*aNumChainsToFill[tGold].aDen) then begin
    aOrder[2] := tGold;
    aOrder[1] := tCoal;
  end else begin
    aOrder[2] := tCoal;
    aOrder[1] := tGold;
  end;

  if (aNumChainsToFill[tIron].aNum*aNumChainsToFill[aOrder[2]].aDen) > (aNumChainsToFill[aOrder[2]].aNum*aNumChainsToFill[tIron].aDen) then begin
    aOrder[0] := aOrder[1];
    aOrder[1] := aOrder[2];
    aOrder[2] := tIron;
  end else begin
    if (aNumChainsToFill[tIron].aNum*aNumChainsToFill[aOrder[1]].aDen) > (aNumChainsToFill[aOrder[1]].aNum*aNumChainsToFill[tIron].aDen) then begin
      aOrder[0] := aOrder[1];
      aOrder[1] := tIron;
    end else begin
      aOrder[0] := tIron;
    end;
  end;

  iJBuildTime := aGetJBuildTime(aWarrior, aPlayer, aOrder);

  aEquipPhase[aPlayer][aWarrior][0].aWhich := tFertile;
  for i := 1 to 3 do aEquipPhase[aPlayer][aWarrior][i].aWhich := aOrder[i-1];

  if aNumChainsToFill[aOrder[0]].aDen > 0 then aEquipPhase[aPlayer][aWarrior][0].aDuration := ((iJBuildTime[0]*aNumChainsToFill[aOrder[0]].aNum) div aNumChainsToFill[aOrder[0]].aDen)
  else aEquipPhase[aPlayer][aWarrior][0].aDuration := 0;
  if aEquipPhase[aPlayer][aWarrior][0].aDuration > aTotalTime then begin
    aEquipPhase[aPlayer][aWarrior][0].aDuration := aTotalTime;
    for i := 1 to 3 do aEquipPhase[aPlayer][aWarrior][i].aDuration := 0;
  end else begin
    i := 1;
    if aNumChainsToFill[aOrder[i-1]].aDen*aNumChainsToFill[aOrder[i]].aDen > 0 then aEquipPhase[aPlayer][aWarrior][i].aDuration := ((iJBuildTime[i]*(aNumChainsToFill[aOrder[i]].aNum*aNumChainsToFill[aOrder[i-1]].aDen-aNumChainsToFill[aOrder[i-1]].aNum*aNumChainsToFill[aOrder[i]].aDen)) div (aNumChainsToFill[aOrder[i-1]].aDen*aNumChainsToFill[aOrder[i]].aDen))
    else aEquipPhase[aPlayer][aWarrior][i].aDuration := 0;

    if aEquipPhase[aPlayer][aWarrior][1].aDuration > (aTotalTime-aEquipPhase[aPlayer][aWarrior][0].aDuration) then begin
      aEquipPhase[aPlayer][aWarrior][1].aDuration := aTotalTime-aEquipPhase[aPlayer][aWarrior][0].aDuration;
      for i := 2 to 3 do aEquipPhase[aPlayer][aWarrior][i].aDuration := 0;
    end else begin
      i := 2;
      if aNumChainsToFill[aOrder[i-1]].aDen*aNumChainsToFill[aOrder[i]].aDen > 0 then aEquipPhase[aPlayer][aWarrior][i].aDuration := ((iJBuildTime[i]*(aNumChainsToFill[aOrder[i]].aNum*aNumChainsToFill[aOrder[i-1]].aDen-aNumChainsToFill[aOrder[i-1]].aNum*aNumChainsToFill[aOrder[i]].aDen)) div (aNumChainsToFill[aOrder[i-1]].aDen*aNumChainsToFill[aOrder[i]].aDen))
      else aEquipPhase[aPlayer][aWarrior][i].aDuration := 0;

      if aEquipPhase[aPlayer][aWarrior][2].aDuration > (aTotalTime-(aEquipPhase[aPlayer][aWarrior][0].aDuration+aEquipPhase[aPlayer][aWarrior][1].aDuration)) then begin
        aEquipPhase[aPlayer][aWarrior][2].aDuration := aTotalTime-(aEquipPhase[aPlayer][aWarrior][0].aDuration+aEquipPhase[aPlayer][aWarrior][1].aDuration);
        aEquipPhase[aPlayer][aWarrior][3].aDuration := 0;

      end else aEquipPhase[aPlayer][aWarrior][3].aDuration := aTotalTime-(aEquipPhase[aPlayer][aWarrior][0].aDuration+aEquipPhase[aPlayer][aWarrior][1].aDuration+aEquipPhase[aPlayer][aWarrior][2].aDuration);

    end;
  end;

  with aEquipPhase[aPlayer][aWarrior][0] do aRecruited := Round(64.4444*aDuration*(  (aMax(aDuration-iJBuildTime[0], 0)/(2*iJBuildTime[0])) )); //1000*Trained Recruits per second = 64.4444

  with aEquipPhase[aPlayer][aWarrior][1] do aRecruited := Round(64.4444*aDuration*(  (aMax(aDuration-iJBuildTime[1], 0)/(2*iJBuildTime[1])) + (aEquipPhase[aPlayer][aWarrior][0].aDuration/iJBuildTime[0]) ));

  with aEquipPhase[aPlayer][aWarrior][2] do aRecruited := Round(64.4444*aDuration*(  (aMax(aDuration-iJBuildTime[2], 0)/(2*iJBuildTime[2])) + (aEquipPhase[aPlayer][aWarrior][0].aDuration/iJBuildTime[0]+aEquipPhase[aPlayer][aWarrior][1].aDuration/iJBuildTime[1]) ));

  with aEquipPhase[aPlayer][aWarrior][3] do aRecruited := Round(64.4444*aDuration*(  (aMax(aDuration-iJBuildTime[3], 0)/(2*iJBuildTime[3])) + (aEquipPhase[aPlayer][aWarrior][0].aDuration/iJBuildTime[0]+aEquipPhase[aPlayer][aWarrior][1].aDuration/iJBuildTime[1]+aEquipPhase[aPlayer][aWarrior][2].aDuration/iJBuildTime[2]) ));
end;

procedure TMainForm.CheckBox11EditingDone(Sender: TObject);
var
  iUnit: tKaM_Warrior;
begin
  LabeledEdit8.Enabled := not CheckBox11.Checked;
  LabeledEdit9.Enabled := not CheckBox11.Checked;
  LabeledEdit10.Enabled := not CheckBox11.Checked;
  LabeledEdit11.Enabled := not CheckBox11.Checked;
  LabeledEdit12.Enabled := not CheckBox11.Checked;
  LabeledEdit13.Enabled := not CheckBox11.Checked;
  LabeledEdit14.Enabled := not CheckBox11.Checked;

  ComboBox5.Enabled := not CheckBox11.Checked;
  ComboBox6.Enabled := not CheckBox11.Checked;

  if not CheckBox11.Checked then begin
    with aLocs[tEnemy] do begin
      aMaxMines[tGold] := aStrToFrac(LabeledEdit12.Text);
      aDistance[tGold] := aStrToFrac(LabeledEdit11.Text);

      aMaxMines[tIron] := aStrToFrac(LabeledEdit9.Text);
      aDistance[tIron] := aStrToFrac(LabeledEdit8.Text);


      aMaxMines[tCoal] := aStrToFrac(LabeledEdit13.Text);
      aDistance[tCoal] := aStrToFrac(LabeledEdit14.Text);

      aDistance[tFertile] := aStrToFrac(LabeledEdit10.Text);
    end;
  end else aLocs[tEnemy] := aLocs[tPlayer];

  for iUnit := Low(tKaM_Warrior) to High(tKaM_Warrior) do aUpdateRecruited(iUnit, tEnemy);
  aUpdateScheme;
end;

procedure TMainForm.LabeledEditEditingDonePlayer(Sender: TObject);
var
  iUnit: tKaM_Warrior;
begin
  with aLocs[tPlayer] do begin
    aMaxMines[tGold] := aStrToFrac(LabeledEdit3.Text);
    aDistance[tGold] := aStrToFrac(LabeledEdit4.Text);

    aMaxMines[tIron] := aStrToFrac(LabeledEdit2.Text);
    aDistance[tIron] := aStrToFrac(LabeledEdit1.Text);


    aMaxMines[tCoal] := aStrToFrac(LabeledEdit5.Text);
    aDistance[tCoal] := aStrToFrac(LabeledEdit6.Text);

    aDistance[tFertile] := aStrToFrac(LabeledEdit7.Text);
  end;

  for iUnit := Low(tKaM_Warrior) to High(tKaM_Warrior) do aUpdateRecruited(iUnit, tPlayer);
  aUpdateScheme;
end;

procedure TMainForm.LabeledEditEditingDoneEnemy(Sender: TObject);
var
  iUnit: tKaM_Warrior;
begin
  with aLocs[tEnemy] do begin
    aMaxMines[tGold] := aStrToFrac(LabeledEdit12.Text);
    aDistance[tGold] := aStrToFrac(LabeledEdit11.Text);

    aMaxMines[tIron] := aStrToFrac(LabeledEdit9.Text);
    aDistance[tIron] := aStrToFrac(LabeledEdit8.Text);


    aMaxMines[tCoal] := aStrToFrac(LabeledEdit13.Text);
    aDistance[tCoal] := aStrToFrac(LabeledEdit14.Text);

    aDistance[tFertile] := aStrToFrac(LabeledEdit10.Text);
  end;

  for iUnit := Low(tKaM_Warrior) to High(tKaM_Warrior) do aUpdateRecruited(iUnit, tEnemy);
  aUpdateScheme;
end;

function aGetMapStats(aName: String; aLoc: Integer; aPlayer: tPlayerType; aKnowBalanced: Boolean): Integer;
begin
  if aName = 'A Midwinter''s Day' then begin
    if aKnowBalanced then result := 1
    else result := 6;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(56, 6);
      aMaxMines[tIron] := aGetFrac(33, 6);
      aMaxMines[tCoal] := aGetFrac(203, 6);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1833, 100);
          aDistance[tIron] := aGetFrac(2516, 100);
          aDistance[tCoal] := aGetFrac(1533, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'A War of Justice' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(71, 8);
      aMaxMines[tIron] := aGetFrac(36, 8);
      aMaxMines[tCoal] := aGetFrac(272, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1912, 100);
          aDistance[tIron] := aGetFrac(1962, 100);
          aDistance[tCoal] := aGetFrac(1850, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Abrak' then begin
    if aKnowBalanced then result := 1
    else result := 4;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(37, 4);
      aMaxMines[tIron] := aGetFrac(26, 4);
      aMaxMines[tCoal] := aGetFrac(162, 4);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1850, 100);
          aDistance[tIron] := aGetFrac(4400, 100);
          aDistance[tCoal] := aGetFrac(2250, 100);
          aDistance[tFertile] := aGetFrac(125, 100);
        end;

      end;
    end;
  end;

  if aName = 'Across the Desert' then begin
    if aKnowBalanced then result := 1
    else result := 6;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(29, 6);
      aMaxMines[tIron] := aGetFrac(30, 6);
      aMaxMines[tCoal] := aGetFrac(164, 6);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2350, 100);
          aDistance[tIron] := aGetFrac(1583, 100);
          aDistance[tCoal] := aGetFrac(1866, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Alice' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(89, 8);
      aMaxMines[tIron] := aGetFrac(51, 8);
      aMaxMines[tCoal] := aGetFrac(447, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2425, 100);
          aDistance[tIron] := aGetFrac(2425, 100);
          aDistance[tCoal] := aGetFrac(725, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Amphibian' then begin
    if aKnowBalanced then result := 1
    else result := 2;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(10, 2);
      aMaxMines[tIron] := aGetFrac(6, 2);
      aMaxMines[tCoal] := aGetFrac(49, 2);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1700, 100);
          aDistance[tIron] := aGetFrac(2700, 100);
          aDistance[tCoal] := aGetFrac(1300, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Annie' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(126, 8);
      aMaxMines[tIron] := aGetFrac(68, 8);
      aMaxMines[tCoal] := aGetFrac(278, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2900, 100);
          aDistance[tIron] := aGetFrac(2612, 100);
          aDistance[tCoal] := aGetFrac(1787, 100);
          aDistance[tFertile] := aGetFrac(187, 100);
        end;

      end;
    end;
  end;

  if aName = 'Babylon' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(41, 8);
      aMaxMines[tIron] := aGetFrac(22, 8);
      aMaxMines[tCoal] := aGetFrac(0, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2125, 100);
          aDistance[tIron] := aGetFrac(2412, 100);
          aDistance[tCoal] := aGetFrac(0, 100);
          aDistance[tFertile] := aGetFrac(312, 100);
        end;

      end;
    end;
  end;

  if aName = 'Back in the Desert' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(45, 8);
      aMaxMines[tIron] := aGetFrac(41, 8);
      aMaxMines[tCoal] := aGetFrac(273, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1850, 100);
          aDistance[tIron] := aGetFrac(2537, 100);
          aDistance[tCoal] := aGetFrac(1837, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Battle Sun' then begin
    if aKnowBalanced then result := 1
    else result := 4;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(22, 4);
      aMaxMines[tIron] := aGetFrac(0, 4);
      aMaxMines[tCoal] := aGetFrac(104, 4);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1475, 100);
          aDistance[tIron] := aGetFrac(0, 100);
          aDistance[tCoal] := aGetFrac(1975, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Blood and Ice' then begin
    if aKnowBalanced then result := 1
    else result := 3;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(18, 3);
      aMaxMines[tIron] := aGetFrac(15, 3);
      aMaxMines[tCoal] := aGetFrac(110, 3);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2166, 100);
          aDistance[tIron] := aGetFrac(3033, 100);
          aDistance[tCoal] := aGetFrac(1966, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Blood River' then begin
    if aKnowBalanced then result := 1
    else result := 6;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(16, 6);
      aMaxMines[tIron] := aGetFrac(18, 6);
      aMaxMines[tCoal] := aGetFrac(0, 6);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2083, 100);
          aDistance[tIron] := aGetFrac(4300, 100);
          aDistance[tCoal] := aGetFrac(12333, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Border Rivers' then begin
    if aKnowBalanced then result := 1
    else result := 4;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(33, 4);
      aMaxMines[tIron] := aGetFrac(40, 4);
      aMaxMines[tCoal] := aGetFrac(202, 4);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2550, 100);
          aDistance[tIron] := aGetFrac(3275, 100);
          aDistance[tCoal] := aGetFrac(2200, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Bridge Disaster' then begin
    if aKnowBalanced then result := 1
    else result := 4;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(9, 4);
      aMaxMines[tIron] := aGetFrac(56, 4);
      aMaxMines[tCoal] := aGetFrac(165, 4);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(7000, 100);
          aDistance[tIron] := aGetFrac(2000, 100);
          aDistance[tCoal] := aGetFrac(1850, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Canyon' then begin
    if aKnowBalanced then result := 1
    else result := 2;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(10, 2);
      aMaxMines[tIron] := aGetFrac(16, 2);
      aMaxMines[tCoal] := aGetFrac(57, 2);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1600, 100);
          aDistance[tIron] := aGetFrac(2300, 100);
          aDistance[tCoal] := aGetFrac(1000, 100);
          aDistance[tFertile] := aGetFrac(300, 100);
        end;

      end;
    end;
  end;

  if aName = 'Castle Slaughter' then begin
    if aKnowBalanced then result := 1
    else result := 6;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(8, 6);
      aMaxMines[tIron] := aGetFrac(0, 6);
      aMaxMines[tCoal] := aGetFrac(0, 6);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(4350, 100);
          aDistance[tIron] := aGetFrac(0, 100);
          aDistance[tCoal] := aGetFrac(0, 100);
          aDistance[tFertile] := aGetFrac(383, 100);
        end;

      end;
    end;
  end;

  if aName = 'Center Castle Looting' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(56, 8);
      aMaxMines[tIron] := aGetFrac(61, 8);
      aMaxMines[tCoal] := aGetFrac(377, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1425, 100);
          aDistance[tIron] := aGetFrac(3912, 100);
          aDistance[tCoal] := aGetFrac(2075, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Coastal Expedition' then begin
    if aKnowBalanced then result := 1
    else result := 6;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(25, 6);
      aMaxMines[tIron] := aGetFrac(27, 6);
      aMaxMines[tCoal] := aGetFrac(181, 6);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1700, 100);
          aDistance[tIron] := aGetFrac(2183, 100);
          aDistance[tCoal] := aGetFrac(1300, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Cold Steel Mountains' then begin
    if aKnowBalanced then result := 1
    else result := 2;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(35, 2);
      aMaxMines[tIron] := aGetFrac(31, 2);
      aMaxMines[tCoal] := aGetFrac(303, 2);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2850, 100);
          aDistance[tIron] := aGetFrac(2100, 100);
          aDistance[tCoal] := aGetFrac(1650, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Cold Water' then begin
    if aKnowBalanced then result := 1
    else result := 6;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(37, 6);
      aMaxMines[tIron] := aGetFrac(44, 6);
      aMaxMines[tCoal] := aGetFrac(122, 6);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(3250, 100);
          aDistance[tIron] := aGetFrac(2350, 100);
          aDistance[tCoal] := aGetFrac(1650, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Crystalline Falls' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(50, 8);
      aMaxMines[tIron] := aGetFrac(50, 8);
      aMaxMines[tCoal] := aGetFrac(255, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1362, 100);
          aDistance[tIron] := aGetFrac(2150, 100);
          aDistance[tCoal] := aGetFrac(1700, 100);
          aDistance[tFertile] := aGetFrac(200, 100);
        end;

      end;
    end;
  end;

  if aName = 'Cube' then begin
    if aKnowBalanced then result := 1
    else result := 12;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(51, 12);
      aMaxMines[tIron] := aGetFrac(94, 12);
      aMaxMines[tCoal] := aGetFrac(555, 12);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2733, 100);
          aDistance[tIron] := aGetFrac(2908, 100);
          aDistance[tCoal] := aGetFrac(1733, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Cursed Ravine' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(65, 8);
      aMaxMines[tIron] := aGetFrac(31, 8);
      aMaxMines[tCoal] := aGetFrac(177, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2625, 100);
          aDistance[tIron] := aGetFrac(2787, 100);
          aDistance[tCoal] := aGetFrac(1875, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Dance of Death' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(34, 8);
      aMaxMines[tIron] := aGetFrac(31, 8);
      aMaxMines[tCoal] := aGetFrac(237, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2025, 100);
          aDistance[tIron] := aGetFrac(2362, 100);
          aDistance[tCoal] := aGetFrac(1125, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Dead of Winter' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(64, 8);
      aMaxMines[tIron] := aGetFrac(32, 8);
      aMaxMines[tCoal] := aGetFrac(290, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2125, 100);
          aDistance[tIron] := aGetFrac(2625, 100);
          aDistance[tCoal] := aGetFrac(1700, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Dead Rivers' then begin
    if aKnowBalanced then result := 1
    else result := 4;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(96, 4);
      aMaxMines[tIron] := aGetFrac(22, 4);
      aMaxMines[tCoal] := aGetFrac(273, 4);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1625, 100);
          aDistance[tIron] := aGetFrac(1850, 100);
          aDistance[tCoal] := aGetFrac(1000, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Defending the Homeland' then begin
    if aKnowBalanced then result := 1
    else result := 6;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(60, 6);
      aMaxMines[tIron] := aGetFrac(25, 6);
      aMaxMines[tCoal] := aGetFrac(182, 6);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1666, 100);
          aDistance[tIron] := aGetFrac(1983, 100);
          aDistance[tCoal] := aGetFrac(1333, 100);
          aDistance[tFertile] := aGetFrac(250, 100);
        end;

      end;
    end;
  end;

  if aName = 'Drastic Measures' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(47, 8);
      aMaxMines[tIron] := aGetFrac(40, 8);
      aMaxMines[tCoal] := aGetFrac(227, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2025, 100);
          aDistance[tIron] := aGetFrac(2250, 100);
          aDistance[tCoal] := aGetFrac(1725, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Ending the Tyranny' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(58, 8);
      aMaxMines[tIron] := aGetFrac(44, 8);
      aMaxMines[tCoal] := aGetFrac(248, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2200, 100);
          aDistance[tIron] := aGetFrac(2362, 100);
          aDistance[tCoal] := aGetFrac(1350, 100);
          aDistance[tFertile] := aGetFrac(112, 100);
        end;

      end;
    end;
  end;

  if aName = 'Eruption' then begin
    if aKnowBalanced then result := 1
    else result := 6;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(69, 6);
      aMaxMines[tIron] := aGetFrac(26, 6);
      aMaxMines[tCoal] := aGetFrac(199, 6);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2250, 100);
          aDistance[tIron] := aGetFrac(2566, 100);
          aDistance[tCoal] := aGetFrac(2016, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Fire of the Hell' then begin
    if aKnowBalanced then result := 1
    else result := 2;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(27, 2);
      aMaxMines[tIron] := aGetFrac(33, 2);
      aMaxMines[tCoal] := aGetFrac(105, 2);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1500, 100);
          aDistance[tIron] := aGetFrac(3100, 100);
          aDistance[tCoal] := aGetFrac(1600, 100);
          aDistance[tFertile] := aGetFrac(200, 100);
        end;

      end;
    end;
  end;

  if aName = 'Forgotten Lands' then begin
    if aKnowBalanced then result := 1
    else result := 6;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(45, 6);
      aMaxMines[tIron] := aGetFrac(30, 6);
      aMaxMines[tCoal] := aGetFrac(219, 6);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(3433, 100);
          aDistance[tIron] := aGetFrac(3250, 100);
          aDistance[tCoal] := aGetFrac(1416, 100);
          aDistance[tFertile] := aGetFrac(633, 100);
        end;

      end;
    end;
  end;

  if aName = 'Frozen Waters' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(30, 8);
      aMaxMines[tIron] := aGetFrac(28, 8);
      aMaxMines[tCoal] := aGetFrac(293, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1637, 100);
          aDistance[tIron] := aGetFrac(2650, 100);
          aDistance[tCoal] := aGetFrac(1150, 100);
          aDistance[tFertile] := aGetFrac(212, 100);
        end;

      end;
    end;
  end;

  if aName = 'Golden Cliffs' then begin
    if aKnowBalanced then result := 1
    else result := 6;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(34, 6);
      aMaxMines[tIron] := aGetFrac(22, 6);
      aMaxMines[tCoal] := aGetFrac(147, 6);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1966, 100);
          aDistance[tIron] := aGetFrac(1716, 100);
          aDistance[tCoal] := aGetFrac(1683, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Horseshoe' then begin
    if aKnowBalanced then result := 1
    else result := 2;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(8, 2);
      aMaxMines[tIron] := aGetFrac(7, 2);
      aMaxMines[tCoal] := aGetFrac(24, 2);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2050, 100);
          aDistance[tIron] := aGetFrac(5400, 100);
          aDistance[tCoal] := aGetFrac(800, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Iron&Gold' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(43, 8);
      aMaxMines[tIron] := aGetFrac(29, 8);
      aMaxMines[tCoal] := aGetFrac(207, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1987, 100);
          aDistance[tIron] := aGetFrac(2537, 100);
          aDistance[tCoal] := aGetFrac(1475, 100);
          aDistance[tFertile] := aGetFrac(150, 100);
        end;

      end;
    end;
  end;

  if aName = 'Land of Hills' then begin
    if aKnowBalanced then result := 1
    else result := 6;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(55, 6);
      aMaxMines[tIron] := aGetFrac(42, 6);
      aMaxMines[tCoal] := aGetFrac(340, 6);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1616, 100);
          aDistance[tIron] := aGetFrac(2500, 100);
          aDistance[tCoal] := aGetFrac(1983, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Lost in the Sands' then begin
    if aKnowBalanced then result := 1
    else result := 2;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(22, 2);
      aMaxMines[tIron] := aGetFrac(8, 2);
      aMaxMines[tCoal] := aGetFrac(59, 2);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1650, 100);
          aDistance[tIron] := aGetFrac(1800, 100);
          aDistance[tCoal] := aGetFrac(1700, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Mega Land' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(91, 8);
      aMaxMines[tIron] := aGetFrac(43, 8);
      aMaxMines[tCoal] := aGetFrac(261, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2337, 100);
          aDistance[tIron] := aGetFrac(2387, 100);
          aDistance[tCoal] := aGetFrac(1700, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Mountainous Region' then begin
    if aKnowBalanced then result := 1
    else result := 4;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(35, 4);
      aMaxMines[tIron] := aGetFrac(26, 4);
      aMaxMines[tCoal] := aGetFrac(206, 4);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(3050, 100);
          aDistance[tIron] := aGetFrac(3650, 100);
          aDistance[tCoal] := aGetFrac(1800, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Neighborhood Clash' then begin
    if aKnowBalanced then result := 1
    else result := 4;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(17, 4);
      aMaxMines[tIron] := aGetFrac(12, 4);
      aMaxMines[tCoal] := aGetFrac(78, 4);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(850, 100);
          aDistance[tIron] := aGetFrac(2300, 100);
          aDistance[tCoal] := aGetFrac(350, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'New Horizon' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(58, 8);
      aMaxMines[tIron] := aGetFrac(36, 8);
      aMaxMines[tCoal] := aGetFrac(168, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2512, 100);
          aDistance[tIron] := aGetFrac(2062, 100);
          aDistance[tCoal] := aGetFrac(1137, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Nibenay Basin' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(58, 8);
      aMaxMines[tIron] := aGetFrac(49, 8);
      aMaxMines[tCoal] := aGetFrac(288, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1775, 100);
          aDistance[tIron] := aGetFrac(2175, 100);
          aDistance[tCoal] := aGetFrac(1437, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Paradise Island' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(45, 8);
      aMaxMines[tIron] := aGetFrac(39, 8);
      aMaxMines[tCoal] := aGetFrac(269, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1962, 100);
          aDistance[tIron] := aGetFrac(5162, 100);
          aDistance[tCoal] := aGetFrac(1425, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Rebound' then begin
    if aKnowBalanced then result := 1
    else result := 6;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(42, 6);
      aMaxMines[tIron] := aGetFrac(20, 6);
      aMaxMines[tCoal] := aGetFrac(155, 6);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1583, 100);
          aDistance[tIron] := aGetFrac(1616, 100);
          aDistance[tCoal] := aGetFrac(833, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Rich Land' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(55, 8);
      aMaxMines[tIron] := aGetFrac(35, 8);
      aMaxMines[tCoal] := aGetFrac(284, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2550, 100);
          aDistance[tIron] := aGetFrac(3000, 100);
          aDistance[tCoal] := aGetFrac(1450, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Shadow Realm' then begin
    if aKnowBalanced then result := 1
    else result := 6;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(56, 6);
      aMaxMines[tIron] := aGetFrac(19, 6);
      aMaxMines[tCoal] := aGetFrac(150, 6);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1700, 100);
          aDistance[tIron] := aGetFrac(2166, 100);
          aDistance[tCoal] := aGetFrac(1850, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Sharp Land' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(39, 8);
      aMaxMines[tIron] := aGetFrac(23, 8);
      aMaxMines[tCoal] := aGetFrac(172, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1750, 100);
          aDistance[tIron] := aGetFrac(2937, 100);
          aDistance[tCoal] := aGetFrac(1162, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Swan Hill' then begin
    if aKnowBalanced then result := 1
    else result := 6;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(79, 6);
      aMaxMines[tIron] := aGetFrac(45, 6);
      aMaxMines[tCoal] := aGetFrac(253, 6);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1533, 100);
          aDistance[tIron] := aGetFrac(3466, 100);
          aDistance[tCoal] := aGetFrac(1433, 100);
          aDistance[tFertile] := aGetFrac(133, 100);
        end;

      end;
    end;
  end;

  if aName = 'Tale of Two Lands' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(94, 8);
      aMaxMines[tIron] := aGetFrac(37, 8);
      aMaxMines[tCoal] := aGetFrac(292, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2550, 100);
          aDistance[tIron] := aGetFrac(3925, 100);
          aDistance[tCoal] := aGetFrac(1837, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'The Final Frontier' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(62, 8);
      aMaxMines[tIron] := aGetFrac(51, 8);
      aMaxMines[tCoal] := aGetFrac(343, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2187, 100);
          aDistance[tIron] := aGetFrac(2425, 100);
          aDistance[tCoal] := aGetFrac(1425, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'The Same Rocks' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(77, 8);
      aMaxMines[tIron] := aGetFrac(56, 8);
      aMaxMines[tCoal] := aGetFrac(395, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2225, 100);
          aDistance[tIron] := aGetFrac(6237, 100);
          aDistance[tCoal] := aGetFrac(2000, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'The Valley of Dangers 2' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(42, 8);
      aMaxMines[tIron] := aGetFrac(73, 8);
      aMaxMines[tCoal] := aGetFrac(264, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2800, 100);
          aDistance[tIron] := aGetFrac(1850, 100);
          aDistance[tCoal] := aGetFrac(3200, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Twin Peaks' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(102, 8);
      aMaxMines[tIron] := aGetFrac(22, 8);
      aMaxMines[tCoal] := aGetFrac(299, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2937, 100);
          aDistance[tIron] := aGetFrac(5662, 100);
          aDistance[tCoal] := aGetFrac(1012, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Valley of the Equilibrium 8P' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(61, 8);
      aMaxMines[tIron] := aGetFrac(54, 8);
      aMaxMines[tCoal] := aGetFrac(479, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1575, 100);
          aDistance[tIron] := aGetFrac(2775, 100);
          aDistance[tCoal] := aGetFrac(2375, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Valley of the Equilibrium' then begin
    if aKnowBalanced then result := 1
    else result := 4;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(29, 4);
      aMaxMines[tIron] := aGetFrac(31, 4);
      aMaxMines[tCoal] := aGetFrac(302, 4);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1600, 100);
          aDistance[tIron] := aGetFrac(2775, 100);
          aDistance[tCoal] := aGetFrac(2300, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Volcanic Violence' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(126, 8);
      aMaxMines[tIron] := aGetFrac(47, 8);
      aMaxMines[tCoal] := aGetFrac(377, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2500, 100);
          aDistance[tIron] := aGetFrac(2562, 100);
          aDistance[tCoal] := aGetFrac(1912, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Volcano Valley' then begin
    if aKnowBalanced then result := 1
    else result := 8;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(65, 8);
      aMaxMines[tIron] := aGetFrac(27, 8);
      aMaxMines[tCoal] := aGetFrac(242, 8);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2275, 100);
          aDistance[tIron] := aGetFrac(3862, 100);
          aDistance[tCoal] := aGetFrac(2375, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Warfare in the Wilderness' then begin
    if aKnowBalanced then result := 1
    else result := 4;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(25, 4);
      aMaxMines[tIron] := aGetFrac(23, 4);
      aMaxMines[tCoal] := aGetFrac(185, 4);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(3275, 100);
          aDistance[tIron] := aGetFrac(3550, 100);
          aDistance[tCoal] := aGetFrac(1375, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Welcome to the Jungle' then begin
    if aKnowBalanced then result := 1
    else result := 2;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(18, 2);
      aMaxMines[tIron] := aGetFrac(4, 2);
      aMaxMines[tCoal] := aGetFrac(24, 2);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(1500, 100);
          aDistance[tIron] := aGetFrac(2250, 100);
          aDistance[tCoal] := aGetFrac(1950, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;

  if aName = 'Wilderness' then begin
    if aKnowBalanced then result := 1
    else result := 4;

    with aLocs[aPlayer] do begin
      aMaxMines[tGold] := aGetFrac(55, 4);
      aMaxMines[tIron] := aGetFrac(52, 4);
      aMaxMines[tCoal] := aGetFrac(133, 4);

      case aLoc of
        1: begin
          aDistance[tGold] := aGetFrac(2825, 100);
          aDistance[tIron] := aGetFrac(1650, 100);
          aDistance[tCoal] := aGetFrac(1900, 100);
          aDistance[tFertile] := aGetFrac(100, 100);
        end;

      end;
    end;
  end;
end;

procedure TMainForm.ComboBox7Change(Sender: TObject);
var
  iUnit: tKaM_Warrior;
begin
  if ComboBox7.ItemIndex > 0 then begin
    aGetMapStats(ComboBox4.Items.Strings[ComboBox4.ItemIndex], ComboBox7.ItemIndex, tPlayer, False);
  end else begin
    with aLocs[tPlayer] do begin
      aMaxMines[tGold] := aGetFrac(0, 1);
      aDistance[tGold] := aGetFrac(0, 1);

      aMaxMines[tIron] := aGetFrac(0, 1);
      aDistance[tIron] := aGetFrac(0, 1);

      aMaxMines[tCoal] := aGetFrac(0, 1);
      aDistance[tCoal] := aGetFrac(0, 1);

      aDistance[tFertile] := aGetFrac(0, 1);
    end;
  end;

  for iUnit := Low(tKaM_Warrior) to High(tKaM_Warrior) do aUpdateRecruited(iUnit, tPlayer);
  aUpdateScheme;
end;

procedure TMainForm.ComboBox8Change(Sender: TObject);
var
  iUnit: tKaM_Warrior;
begin
  if ComboBox8.ItemIndex > 0 then begin
    aGetMapStats(ComboBox4.Items.Strings[ComboBox4.ItemIndex], ComboBox8.ItemIndex, tEnemy, False);
  end else begin
    with aLocs[tEnemy] do begin
      aMaxMines[tGold] := aGetFrac(0, 1);
      aDistance[tGold] := aGetFrac(0, 1);

      aMaxMines[tIron] := aGetFrac(0, 1);
      aDistance[tIron] := aGetFrac(0, 1);

      aMaxMines[tCoal] := aGetFrac(0, 1);
      aDistance[tCoal] := aGetFrac(0, 1);

      aDistance[tFertile] := aGetFrac(0, 1);
    end;
  end;

  for iUnit := Low(tKaM_Warrior) to High(tKaM_Warrior) do aUpdateRecruited(iUnit, tEnemy);
  aUpdateScheme;
end;

procedure TMainForm.ComboBox4Change(Sender: TObject);
var
  iUnit: tKaM_Warrior;
  i: Integer;
begin
  if ComboBox4.ItemIndex = 0 then begin
    LabeledEdit1.Enabled := True;
    LabeledEdit2.Enabled := True;
    LabeledEdit3.Enabled := True;
    LabeledEdit4.Enabled := True;
    LabeledEdit5.Enabled := True;
    LabeledEdit6.Enabled := True;
    LabeledEdit7.Enabled := True;

    CheckBox11.Enabled := True;

    Label28.Visible := False;
    ComboBox7.Visible := False;
    Label31.Visible := False;
    ComboBox8.Visible := False;

    with aLocs[tPlayer] do begin
      aMaxMines[tGold] := aStrToFrac(LabeledEdit3.Text);
      aDistance[tGold] := aStrToFrac(LabeledEdit4.Text);

      aMaxMines[tIron] := aStrToFrac(LabeledEdit2.Text);
      aDistance[tIron] := aStrToFrac(LabeledEdit1.Text);


      aMaxMines[tCoal] := aStrToFrac(LabeledEdit5.Text);
      aDistance[tCoal] := aStrToFrac(LabeledEdit6.Text);

      aDistance[tFertile] := aStrToFrac(LabeledEdit7.Text);
    end;

    for iUnit := Low(tKaM_Warrior) to High(tKaM_Warrior) do aUpdateRecruited(iUnit, tPlayer);

    CheckBox11EditingDone(CheckBox11); //Also updates the scheme
  end else begin
    LabeledEdit1.Enabled := False;
    LabeledEdit2.Enabled := False;
    LabeledEdit3.Enabled := False;
    LabeledEdit4.Enabled := False;
    LabeledEdit5.Enabled := False;
    LabeledEdit6.Enabled := False;
    LabeledEdit7.Enabled := False;

    CheckBox11.Enabled := False;

    LabeledEdit8.Enabled := False;
    LabeledEdit9.Enabled := False;
    LabeledEdit10.Enabled := False;
    LabeledEdit11.Enabled := False;
    LabeledEdit12.Enabled := False;
    LabeledEdit13.Enabled := False;
    LabeledEdit14.Enabled := False;

    if aGetMapStats(ComboBox4.Items.Strings[ComboBox4.ItemIndex], 0, tPlayer, True) = 1 then begin //Balanced map
      ComboBox5.Enabled := False;
      ComboBox6.Enabled := False;
      Label28.Visible := False;
      ComboBox7.Visible := False;
      Label31.Visible := False;
      ComboBox8.Visible := False;

      aGetMapStats(ComboBox4.Items.Strings[ComboBox4.ItemIndex], 1, tPlayer, False);

      aLocs[tEnemy] := aLocs[tPlayer];

      for iUnit := Low(tKaM_Warrior) to High(tKaM_Warrior) do aUpdateRecruited(iUnit, tPlayer);
      for iUnit := Low(tKaM_Warrior) to High(tKaM_Warrior) do aUpdateRecruited(iUnit, tEnemy);
      aUpdateScheme;

    end else begin //Unbalanced map
      ComboBox5.Enabled := True;
      ComboBox6.Enabled := True;
      Label28.Visible := True;
      ComboBox7.Visible := True;
      Label31.Visible := True;
      ComboBox8.Visible := True;

      with aLocs[tPlayer] do begin
        aMaxMines[tGold] := aGetFrac(0, 1);
        aDistance[tGold] := aGetFrac(0, 1);

        aMaxMines[tIron] := aGetFrac(0, 1);
        aDistance[tIron] := aGetFrac(0, 1);

        aMaxMines[tCoal] := aGetFrac(0, 1);
        aDistance[tCoal] := aGetFrac(0, 1);

        aDistance[tFertile] := aGetFrac(0, 1);
      end;

      aLocs[tEnemy] := aLocs[tPlayer];

      ComboBox7.Items.Clear;
      ComboBox7.Items.Add('n/d');

      ComboBox8.Items.Clear;
      ComboBox8.Items.Add('n/d');

      for i := 1 to aGetMapStats(ComboBox4.Items.Strings[ComboBox4.ItemIndex], 0, tPlayer, False) do begin
        ComboBox7.Items.Add(IntToStr(i));
        ComboBox8.Items.Add(IntToStr(i));
      end;

      ComboBox7.ItemIndex := 0;
      ComboBox8.ItemIndex := 0;

      aUpdateScheme;
    end;
  end;
end;

function aGetRecruited(aWarrior: tKaM_Warrior; aPlayer: tPlayerType; aTimeStart, aTimeEnd: Int64): Int64;
var
  iT, iT2: Int64;
  i: Integer;
begin
  iT := 0;
  result := 0;

  for i := 0 to 3 do with aEquipPhase[aPlayer][aWarrior][i] do if aDuration > 0 then begin
    iT := iT+aDuration;
    if iT <= aTimeEnd then begin
      result := result+aRecruited;
    end else begin
      iT2 := aTimeEnd-iT+aDuration;
      result := result+Round(aRecruited*iT2/aDuration);
      Break;
    end;
  end;

  iT := 0;

  if aTimeStart > 0 then for i := 0 to 3 do with aEquipPhase[aPlayer][aWarrior][i] do if aDuration > 0 then begin
    iT := iT+aDuration;
    if iT <= aTimeStart then begin
      result := result-aRecruited;
    end else begin
      iT2 := aTimeStart-iT+aDuration;
      result := result-Round(aRecruited*iT2/aDuration);
      Break;
    end;
  end;
end;

function aPoint(aX, aY: Integer): TPoint;
begin
  result.X := aX;
  result.Y := aY;
end;

function aWarriorPoint(aWarrior: tKaM_Warrior): TPoint;
begin
  case aWarrior of
    ut_Militia: result := aPoint(590, 328);
    ut_AxeFighter: result := aPoint(65, 236);
    ut_SwordFighter: result := aPoint(185, 562);
    ut_Bowman: result := aPoint(366, 61);
    ut_Crossbowman: result := aPoint(185, 93);
    ut_LanceCarrier: result := aPoint(65, 419);
    ut_Pikeman: result := aPoint(366, 594);
    ut_Scout: result := aPoint(526, 501);
    ut_Knight: result := aPoint(526, 154);
  end;
end;

function aGetColor(aRatio: Integer): TColor; //TColor($000000ff) is red, TColor($0000ff00) is green, TColor($0000ffff) is yellow
var
  i, i2, iRatio: Integer;
begin
  if aRatio > 1000 then iRatio := 1000
  else iRatio := aRatio;

  i := Round(255*iRatio/1000);
  if i > 255 then i := 255;
  if i < 0 then i := 0;

  if aRatio < 1000 then iRatio := 0
  else iRatio := aRatio-1000;

  i2 := 255-Round(255*iRatio/2000);
  if i2 > 255 then i2 := 255;
  if i2 < 0 then i2 := 0;

  result := TColor(i2*256+i);
end;

function aGetRangedEffectiveness(aPlayer: tPlayerType; aRanged, aTarget: tKaM_Warrior): Int64;
var
  iFrac: tFrac;
  iRecruited: Int64;
begin
  iFrac := aGetFrac(1, 1);
  if aTarget in [ut_AxeFighter, ut_Scout] then iFrac := aGetFrac(300, 225);
  if aTarget in [ut_SwordFighter, ut_Knight] then iFrac := aGetFrac(400, 325);

  if ((aRanged = ut_Crossbowman) AND (aPlayer = tPlayer)) OR ((aRanged = ut_Bowman) AND (aPlayer = tEnemy)) then begin
    iRecruited := aGetRecruited(ut_Crossbowman, aPlayer, aStartTime, aTotalTime);
    if iRecruited > 0 then result := Round((1000*aGetRecruited(ut_Bowman, aPlayer, aStartTime, aTotalTime)*iFrac.aDen)/(iRecruited*iFrac.aNum))
    else Result := 3000;
  end else begin
    iRecruited := aGetRecruited(ut_Bowman, aPlayer, aStartTime, aTotalTime);
    if iRecruited > 0 then result := Round((1000*aGetRecruited(ut_Crossbowman, aPlayer, aStartTime, aTotalTime)*iFrac.aNum)/(iRecruited*iFrac.aDen))
    else Result := 3000;
  end;
end;

procedure TMainForm.aDrawArrow(aWarriorPlayer, aWarriorEnemy: tKaM_Warrior);
var
  iPlayerRecruited, iEnemyRecruited, iRatio2, iLength, iDiffX, iDiffY: Int64;
  iRatio: tFrac;
  aPStart, aPTip, aPBase: TPoint;
begin
  if aWarriorPlayer = aWarriorEnemy then Exit;

  if ((aWarriorPlayer in [ut_Bowman, ut_Crossbowman]) AND (aWarriorEnemy in [ut_Bowman, ut_Crossbowman])) OR ( (not(aWarriorPlayer in [ut_Bowman, ut_Crossbowman])) AND (not (aWarriorEnemy in [ut_Bowman, ut_Crossbowman])) ) then begin
    iPlayerRecruited := aGetRecruited(aWarriorPlayer, tPlayer, aStartTime, aTotalTime);
    iEnemyRecruited := aGetRecruited(aWarriorEnemy, tEnemy, aStartTime, aTotalTime);
    iRatio := aGetNumRatio(aWarriorPlayer, aWarriorEnemy);

    if iPlayerRecruited = 0 then begin
      if iEnemyRecruited = 0 then iRatio2 := 1000
      else iRatio2 := 3000;
    end else iRatio2 := Round((1000*iRatio.aNum*iEnemyRecruited)/(iRatio.aDen*iPlayerRecruited));
  end else begin
     if aWarriorPlayer in [ut_Bowman, ut_Crossbowman] then iRatio2 := aGetRangedEffectiveness(tPlayer, aWarriorPlayer, aWarriorEnemy);
     if aWarriorEnemy in [ut_Bowman, ut_Crossbowman] then iRatio2 := aGetRangedEffectiveness(tEnemy, aWarriorEnemy, aWarriorPlayer);
  end;

  if iRatio2 > 3000 then iRatio2 := 3000;
  if iRatio2 < 333 then iRatio2 := 333;

  aPStart := aWarriorPoint(aWarriorPlayer);
  aPTip := aWarriorPoint(aWarriorEnemy);
  iDiffX := aPTip.X-aPStart.X;
  iDiffY := aPTip.Y-aPStart.Y;
  iLength := Round(Sqrt(iDiffX*iDiffX+iDiffY*iDiffY));

  if iLength < 1 then iLength := 1;
  aPStart := aPoint(Round(aPStart.X+45*iDiffX/iLength), Round(aPStart.Y+65*iDiffY/iLength));
  aPTip := aPoint(Round(aPTip.X-45*iDiffX/iLength), Round(aPTip.Y-65*iDiffY/iLength));

  ImageCounters.Canvas.Pen.Color := aGetColor(iRatio2);
  ImageCounters.Canvas.Pen.Width := 10;

  ImageCounters.Canvas.Line(aPStart, aPTip);

  iDiffX := aPTip.X-aPStart.X;
  iDiffY := aPTip.Y-aPStart.Y;
  iLength := Round(Sqrt(iDiffX*iDiffX+iDiffY*iDiffY));
  if iLength < 1 then iLength := 1;

  if iRatio2 < 1250 then begin
    aPBase := aPoint(Round(aPTip.X-20*iDiffX/iLength), Round(aPTip.Y-20*iDiffY/iLength));

    ImageCounters.Canvas.Line(aPTip, aPoint(aPBase.X+Round(10*iDiffY/iLength), aPBase.Y-Round(10*iDiffX/iLength) ));
    ImageCounters.Canvas.Line(aPTip, aPoint(aPBase.X-Round(10*iDiffY/iLength), aPBase.Y+Round(10*iDiffX/iLength) ));
  end;
  if iRatio2 > 800 then begin
    aPBase := aPoint(Round(aPStart.X+20*iDiffX/iLength), Round(aPStart.Y+20*iDiffY/iLength));

    ImageCounters.Canvas.Line(aPStart, aPoint(aPBase.X-Round(10*iDiffY/iLength), aPBase.Y+Round(10*iDiffX/iLength) ));
    ImageCounters.Canvas.Line(aPStart, aPoint(aPBase.X+Round(10*iDiffY/iLength), aPBase.Y-Round(10*iDiffX/iLength) ));
  end;
end;

procedure TMainForm.aUpdateScheme;
var
  aImage: TPortableNetworkGraphic;
  iUnit, iUnit2: tKaM_Warrior;
  i: Integer;
begin
  ImageCounters.Canvas.Brush.Style := bsSolid;
  ImageCounters.Canvas.Brush.Color := clWindow;
  ImageCounters.Canvas.FillRect(0, 0, ImageCounters.Width, ImageCounters.Height);

  if CheckBox11.Checked OR (aGetMapStats(ComboBox4.Items.Strings[ComboBox4.ItemIndex], 0, tPlayer, True) = 1) then begin
    for iUnit := Low(tKaM_Warrior) to High(tKaM_Warrior) do for iUnit2 := tKaM_Warrior(Integer(iUnit)+1) to High(tKaM_Warrior) do aDrawArrow(iUnit, iUnit2);
  end else begin
    if ComboBox5.ItemIndex > 0 then for iUnit := Low(tKaM_Warrior) to High(tKaM_Warrior) do aDrawArrow(tKaM_Warrior(ComboBox5.ItemIndex), iUnit);
    if ComboBox6.ItemIndex > 0 then for iUnit := Low(tKaM_Warrior) to High(tKaM_Warrior) do aDrawArrow(iUnit, tKaM_Warrior(ComboBox6.ItemIndex));
  end;

  aImage := TPortableNetworkGraphic.Create;
  try
    aImage.LoadFromFile('KaM_PICS/Units ring/Units.png');
    ImageCounters.Canvas.Draw(0, 0, aImage);
  finally
    aImage.Free;
  end;

  for i := 1 to 9 do StringGridRecruited.Cells[1, i] := IntToStr(aGetRecruited(tKaM_Warrior(i), tPlayer, aStartTime, aTotalTime) div 1000);
  for i := 1 to 9 do StringGridRecruited.Cells[2, i] := IntToStr(aGetRecruited(tKaM_Warrior(i), tEnemy, aStartTime, aTotalTime) div 1000);
end;


end.
