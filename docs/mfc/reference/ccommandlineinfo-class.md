---
title: Klasa CCommandLineInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCommandLineInfo
- AFXWIN/CCommandLineInfo
- AFXWIN/CCommandLineInfo::CCommandLineInfo
- AFXWIN/CCommandLineInfo::ParseParam
- AFXWIN/CCommandLineInfo::m_bRunAutomated
- AFXWIN/CCommandLineInfo::m_bRunEmbedded
- AFXWIN/CCommandLineInfo::m_bShowSplash
- AFXWIN/CCommandLineInfo::m_nShellCommand
- AFXWIN/CCommandLineInfo::m_strDriverName
- AFXWIN/CCommandLineInfo::m_strFileName
- AFXWIN/CCommandLineInfo::m_strPortName
- AFXWIN/CCommandLineInfo::m_strPrinterName
- AFXWIN/CCommandLineInfo::m_strRestartIdentifier
dev_langs:
- C++
helpviewer_keywords:
- CCommandLineInfo [MFC], CCommandLineInfo
- CCommandLineInfo [MFC], ParseParam
- CCommandLineInfo [MFC], m_bRunAutomated
- CCommandLineInfo [MFC], m_bRunEmbedded
- CCommandLineInfo [MFC], m_bShowSplash
- CCommandLineInfo [MFC], m_nShellCommand
- CCommandLineInfo [MFC], m_strDriverName
- CCommandLineInfo [MFC], m_strFileName
- CCommandLineInfo [MFC], m_strPortName
- CCommandLineInfo [MFC], m_strPrinterName
- CCommandLineInfo [MFC], m_strRestartIdentifier
ms.assetid: 3e313ddb-0a82-4991-87ac-a27feff4668c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f5fd5eb6e4b58cbca21220bf6a7161505505dd3a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080549"
---
# <a name="ccommandlineinfo-class"></a>Klasa CCommandLineInfo

Pomoc podczas analizowania wiersza polecenia przy uruchamianiu aplikacji.

## <a name="syntax"></a>Składnia

```
class CCommandLineInfo : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCommandLineInfo::CCommandLineInfo](#ccommandlineinfo)|Tworzy domyślny `CCommandLineInfo` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCommandLineInfo::ParseParam](#parseparam)|Zastąp to wywołanie zwrotne, można przeanalizować poszczególne parametry.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CCommandLineInfo::m_bRunAutomated](#m_brunautomated)|Określa wiersz polecenia `/Automation` opcja został znaleziony.|
|[CCommandLineInfo::m_bRunEmbedded](#m_brunembedded)|Określa wiersz polecenia `/Embedding` opcja został znaleziony.|
|[CCommandLineInfo::m_bShowSplash](#m_bshowsplash)|Wskazuje, jeśli powinien być wyświetlany ekran powitalny.|
|[CCommandLineInfo::m_nShellCommand](#m_nshellcommand)|Wskazuje polecenia powłoki do przetworzenia.|
|[CCommandLineInfo::m_strDriverName](#m_strdrivername)|Wskazuje sterownik nazwę, jeśli polecenie powłoki Drukuj; w przeciwnym razie jest pusty.|
|[CCommandLineInfo::m_strFileName](#m_strfilename)|Wskazuje nazwę pliku, który może być otwarty lub drukowane; pusty, jeśli nowy lub DDE polecenia powłoki.|
|[CCommandLineInfo::m_strPortName](#m_strportname)|Określa numer portu nazwy, jeśli polecenie powłoki Drukuj; w przeciwnym razie jest pusty.|
|[CCommandLineInfo::m_strPrinterName](#m_strprintername)|Wskazuje drukarki nazwę, jeśli polecenie powłoki Drukuj; w przeciwnym razie jest pusty.|
|[CCommandLineInfo::m_strRestartIdentifier](#m_strrestartidentifier)|Określa identyfikator unikatowy ponownego uruchomienia dla Menedżera ponownego uruchamiania, jeśli Menedżera ponownego uruchamiania ponownego uruchomienia aplikacji.|

## <a name="remarks"></a>Uwagi

Aplikacja MFC zazwyczaj utworzy lokalne wystąpienie tej klasy w [InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) funkcji jego obiektu aplikacji. Ten obiekt jest następnie przekazywany do [CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline), które wielokrotnie wywołuje [ParseParam](#parseparam) do wypełnienia `CCommandLineInfo` obiektu. `CCommandLineInfo` Obiekt jest następnie przekazywany do [CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand) obsługi argumentów wiersza polecenia i flagi.

Ten obiekt jest używany do hermetyzacji poniższych opcji wiersza polecenia i parametry:

|argument wiersza polecenia|Polecenie wykonane|
|----------------------------|----------------------|
|*Aplikacja*|Nowy plik.|
|*Aplikacja* nazwy pliku|Otwórz plik.|
|*Aplikacja* `/p` nazwy pliku|Wydrukuj plik użyta drukarka domyślna.|
|*Aplikacja* `/pt` portu sterownika drukarki nazwy pliku|Wydrukuj plik w określonej drukarki.|
|*Aplikacja* `/dde`|Uruchom i await DDE polecenia.|
|*Aplikacja* `/Automation`|Uruchomiona jako serwer automatyzacji OLE.|
|*Aplikacja* `/Embedding`|Uruchomiona edytować element osadzony OLE.|
|*Aplikacja* `/Register`<br /><br /> *Aplikacja* `/Regserver`|Informuje o aplikacji do wykonywania zadań rejestracji.|
|*Aplikacja* `/Unregister`<br /><br /> *Aplikacja* `/Unregserver`|Informuje o aplikacji do wykonywania wszystkich zadań wyrejestrowanie.|

Klasa nowe z `CCommandLineInfo` aby obsłużyć inne flagi i wartości parametrów. Zastąp [ParseParam](#parseparam) do obsługi nowych znaczników.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CCommandLineInfo`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="ccommandlineinfo"></a>  CCommandLineInfo::CCommandLineInfo

Ten konstruktor tworzy `CCommandLineInfo` obiektu z wartościami domyślnymi.

```
CCommandLineInfo();
```

### <a name="remarks"></a>Uwagi

Wartość domyślna to, aby wyświetlić ekran powitalny ( `m_bShowSplash=TRUE`) i wykonać nowe polecenia menu Plik ( `m_nShellCommand` **= NewFile**).

Struktura wywołuje aplikację [ParseParam](#parseparam) do wypełniania elementów członkowskich danych tego obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#54](../../mfc/codesnippet/cpp/ccommandlineinfo-class_1.cpp)]

##  <a name="m_brunautomated"></a>  CCommandLineInfo::m_bRunAutomated

Oznacza to, że `/Automation` Flaga został znaleziony w wierszu polecenia.

```
BOOL m_bRunAutomated;
```

### <a name="remarks"></a>Uwagi

W przypadku opcji TRUE oznacza to, uruchomiona jako serwer automatyzacji OLE.

##  <a name="m_brunembedded"></a>  CCommandLineInfo::m_bRunEmbedded

Oznacza to, że `/Embedding` Flaga został znaleziony w wierszu polecenia.

```
BOOL m_bRunEmbedded;
```

### <a name="remarks"></a>Uwagi

W przypadku opcji TRUE oznacza to, uruchamiania dla edytowania wbudowanego elementu OLE.

##  <a name="m_bshowsplash"></a>  CCommandLineInfo::m_bShowSplash

Wskazuje, że powinien być wyświetlany na ekranie powitalnym.

```
BOOL m_bShowSplash;
```

### <a name="remarks"></a>Uwagi

W przypadku opcji TRUE oznacza, że ekran powitalny dla tej aplikacji powinien być wyświetlany podczas uruchamiania. Domyślna implementacja klasy [ParseParam](#parseparam) ustawia ten element członkowski danych na wartość TRUE, jeśli [m_nShellCommand](#m_nshellcommand) jest równa `CCommandLineInfo::FileNew`.

##  <a name="m_nshellcommand"></a>  CCommandLineInfo::m_nShellCommand

Wskazuje polecenie powłoki dla tego wystąpienia aplikacji.

```
m_nShellCommand;
```

### <a name="remarks"></a>Uwagi

Typ dla tego elementu członkowskiego danych jest następujący typ wyliczany, która jest zdefiniowana w `CCommandLineInfo` klasy.

```
enum {
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE,
    AppRegister,
    AppUnregister,
    RestartByRestartManager,
    FileNothing = -1
    };
```

Aby uzyskać krótki opis tych wartości zobacz poniżej.

- `CCommandLineInfo::FileNew` Wskazuje, że nazwa pliku nie został znaleziony w wierszu polecenia.

- `CCommandLineInfo::FileOpen` Wskazuje, że w wierszu polecenia można odnaleźć nazwy pliku i żaden z następujących flag znaleziono w wierszu polecenia: `/p`, `/pt`, `/dde`.

- `CCommandLineInfo::FilePrint` Oznacza to, że `/p` Flaga został znaleziony w wierszu polecenia.

- `CCommandLineInfo::FilePrintTo` Oznacza to, że `/pt` Flaga został znaleziony w wierszu polecenia.

- `CCommandLineInfo::FileDDE` Oznacza to, że `/dde` Flaga został znaleziony w wierszu polecenia.

- `CCommandLineInfo::AppRegister` Oznacza to, że `/Register` lub `/Regserver` Flaga został znaleziony w wierszu polecenia i zażądano aplikacji do zarejestrowania.

- `CCommandLineInfo::AppUnregister` Oznacza to, że `/Unregister` lub `/Unregserver` aplikacji został poproszony o wyrejestrować.

- `CCommandLineInfo::RestartByRestartManager` Wskazuje, że aplikacja została ponownie uruchomiona przez Menedżera ponownego uruchamiania.

- `CCommandLineInfo::FileNothing` Wyłącza wyświetlanie nowe podrzędne okno MDI przy uruchamianiu. Zgodnie z projektem aplikacji generowanych przez Kreatora aplikacji MDI, należy wyświetlić nowe podrzędne okno przy uruchamianiu. Aby wyłączyć tę funkcję, aplikacja może użyć `CCommandLineInfo::FileNothing` jako polecenia powłoki, gdy wywołuje [elemencie ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand). `ProcessShellCommand` jest wywoływana przez `InitInstance( )` wszystkich `CWinApp` klas pochodnych.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#55](../../mfc/codesnippet/cpp/ccommandlineinfo-class_2.cpp)]

##  <a name="m_strdrivername"></a>  CCommandLineInfo::m_strDriverName

Przechowuje wartość trzeciego parametru bez flagi w wierszu polecenia.

```
CString m_strDriverName;
```

### <a name="remarks"></a>Uwagi

Ten parametr jest zwykle nazwę sterownika drukarki dla polecenia powłoki do drukowania. Domyślna implementacja klasy [ParseParam](#parseparam) ustawia to dane elementu członkowskiego tylko wtedy, gdy `/pt` Flaga został znaleziony w wierszu polecenia.

##  <a name="m_strfilename"></a>  CCommandLineInfo::m_strFileName

Przechowuje wartość pierwszego parametru bez flagi w wierszu polecenia.

```
CString m_strFileName;
```

### <a name="remarks"></a>Uwagi

Ten parametr jest zwykle nazwę pliku, aby otworzyć.

##  <a name="m_strportname"></a>  CCommandLineInfo::m_strPortName

Przechowuje wartość czwartego parametru bez flagi w wierszu polecenia.

```
CString m_strPortName;
```

### <a name="remarks"></a>Uwagi

Ten parametr jest zwykle nazwa portu drukarki dla polecenia powłoki do drukowania. Domyślna implementacja klasy [ParseParam](#parseparam) ustawia to dane elementu członkowskiego tylko wtedy, gdy `/pt` Flaga został znaleziony w wierszu polecenia.

##  <a name="m_strprintername"></a>  CCommandLineInfo::m_strPrinterName

Przechowuje wartość drugiego parametru bez flagi w wierszu polecenia.

```
CString m_strPrinterName;
```

### <a name="remarks"></a>Uwagi

Ten parametr jest zwykle nazwę drukarki dla polecenia powłoki do drukowania. Domyślna implementacja klasy [ParseParam](#parseparam) ustawia to dane elementu członkowskiego tylko wtedy, gdy `/pt` Flaga został znaleziony w wierszu polecenia.

##  <a name="m_strrestartidentifier"></a>  CCommandLineInfo::m_strRestartIdentifier

To unikatowy ponownie identyfikator w wierszu polecenia.

```
CString m_strRestartIdentifier;
```

### <a name="remarks"></a>Uwagi

Identyfikator ponowne uruchomienie jest unikatowy dla każdego wystąpienia aplikacji.

Jeśli Menedżera ponownego uruchamiania kończy działanie aplikacji i jest skonfigurowany do ponownego uruchomienia, Menedżera ponownego uruchamiania wykonuje aplikacji z poziomu wiersza polecenia o identyfikatorze ponowne uruchomienie jako parametr opcjonalny. Gdy Menedżera ponownego uruchamiania używa identyfikatora ponownego uruchomienia, aplikacja może ponownie otworzyć wcześniej otwartych dokumentów i odzyskiwać pliki automatycznie zapisany.

##  <a name="parseparam"></a>  CCommandLineInfo::ParseParam

Struktura wywołuje tę funkcję do analizowania/interpretacji poszczególne parametry, z poziomu wiersza polecenia. Druga wersja różni się od pierwszego tylko w projektach Unicode.

```
virtual void ParseParam(
    const char* pszParam,
    BOOL bFlag,
    BOOL bLast);

virtual void ParseParam(
    const TCHAR* pszParam,
    BOOL bFlag,
    BOOL bLast);
```

### <a name="parameters"></a>Parametry

*pszParam*<br/>
Parametr lub flagi.

*bFlag*<br/>
Wskazuje, czy *pszParam* jest parametr lub flagi.

*rażenia*<br/>
Wskazuje, czy jest ostatni parametr lub flagi w wierszu polecenia.

### <a name="remarks"></a>Uwagi

[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline) wywołania `ParseParam` jeden raz dla każdego parametru lub flagi w wierszu polecenia, przekazywanie argumentu *pszParam*. Jeśli pierwszym znakiem parametru jest " **-**"lub " **/**", a następnie jest usuwany i *bFlag* jest ustawiona na wartość TRUE. Podczas analizowania ostatni parametr *rażenia* jest ustawiona na wartość TRUE.

Domyślna implementacja tej funkcji rozpoznaje następujących flag: `/p`, `/pt`, `/dde`, `/Automation`, i `/Embedding`, jak pokazano w poniższej tabeli:

|argument wiersza polecenia|Polecenie wykonane|
|----------------------------|----------------------|
|*Aplikacja*|Nowy plik.|
|*Aplikacja* nazwy pliku|Otwórz plik.|
|*Aplikacja* `/p` nazwy pliku|Wydrukuj plik użyta drukarka domyślna.|
|*Aplikacja* `/pt` portu sterownika drukarki nazwy pliku|Wydrukuj plik w określonej drukarki.|
|*Aplikacja* `/dde`|Uruchom i await DDE polecenia.|
|*Aplikacja* `/Automation`|Uruchomiona jako serwer automatyzacji OLE.|
|*Aplikacja* `/Embedding`|Uruchomiona edytować element osadzony OLE.|
|*Aplikacja* `/Register`<br /><br /> *Aplikacja* `/Regserver`|Informuje o aplikacji do wykonywania zadań rejestracji.|
|*Aplikacja* `/Unregister`<br /><br /> *Aplikacja* `/Unregserver`|Informuje o aplikacji do wykonywania wszystkich zadań wyrejestrowanie.|

Te informacje są przechowywane w [m_bRunAutomated](#m_brunautomated), [m_bRunEmbedded](#m_brunembedded), i [m_nShellCommand](#m_nshellcommand). Flagi są oznaczone przez zwykły ukośnik " **/**"lub łącznik" **-**".

Domyślna implementacja umieszcza pierwszy parametr bez flagi do [m_strFileName](#m_strfilename). W przypadku właściwości `/pt` flagi, domyślna implementacja umieszcza drugiego, trzecia i czwarta parametry bez flagi do [m_strPrinterName](#m_strprintername), [m_strDriverName](#m_strdrivername), i [m_ strPortName](#m_strportname), odpowiednio.

Domyślna implementacja ustawia również [m_bShowSplash](#m_bshowsplash) na wartość TRUE tylko w przypadku nowego pliku. W przypadku nowego pliku użytkownik podjęte działania powodujące samej aplikacji. W każdym innym przypadku, w tym otwierania istniejące pliki, korzystając z powłoki akcji użytkownika obejmuje go bezpośrednio. W widzenia zorientowany na ekran powitalny trzeba poinformować o aplikacji, uruchamiania.

Przesłonić tę funkcję w swojej klasie pochodnej, aby obsłużyć inne flagi i wartości parametrów.

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)<br/>
[CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)

