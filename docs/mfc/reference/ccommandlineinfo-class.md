---
title: Klasa CCommandLineInfo
ms.date: 11/04/2016
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
ms.openlocfilehash: 0b4d5e5d253f2eb10388a69286d21e2190826eba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369461"
---
# <a name="ccommandlineinfo-class"></a>Klasa CCommandLineInfo

Pomaga w analizowaniu wiersza polecenia podczas uruchamiania aplikacji.

## <a name="syntax"></a>Składnia

```
class CCommandLineInfo : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCommandLineInfo::CCommandLineInfo](#ccommandlineinfo)|Tworzy obiekt `CCommandLineInfo` domyślny.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCommandLineInfo::ParseParam](#parseparam)|Zastąpuj to wywołanie zwrotne, aby przeanalizować poszczególne parametry.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CCommandLineInfo::m_bRunAutomated](#m_brunautomated)|Wskazuje, że została `/Automation` znaleziona opcja wiersza polecenia.|
|[CCommandLineInfo::m_bRunEmbedded](#m_brunembedded)|Wskazuje, że została `/Embedding` znaleziona opcja wiersza polecenia.|
|[CCommandLineInfo::m_bShowSplash](#m_bshowsplash)|Wskazuje, czy powinien być wyświetlany ekran powitalny.|
|[CCommandLineInfo::m_nShellCommand](#m_nshellcommand)|Wskazuje polecenie powłoki do przetworzenia.|
|[CCommandLineInfo::m_strDriverName](#m_strdrivername)|Wskazuje nazwę sterownika, jeśli polecenie powłoki to Drukuj do; w przeciwnym razie puste.|
|[CCommandLineInfo::m_strFileName](#m_strfilename)|Wskazuje nazwę pliku, który ma zostać otwarty lub wydrukowany; puste, jeśli polecenie powłoki to Nowy lub DDE.|
|[CCommandLineInfo::m_strPortName](#m_strportname)|Wskazuje nazwę portu, jeśli polecenie powłoki to Drukuj do; w przeciwnym razie puste.|
|[CCommandLineInfo::m_strPrinterName](#m_strprintername)|Wskazuje nazwę drukarki, jeśli polecenie powłoki to Drukuj do; w przeciwnym razie puste.|
|[CCommandLineInfo::m_strRestartIdentifier](#m_strrestartidentifier)|Wskazuje unikatowy identyfikator ponownego uruchomienia menedżera ponownego uruchamiania, jeśli menedżer ponownego uruchomienia ponownie uruchomi aplikację.|

## <a name="remarks"></a>Uwagi

Aplikacja MFC zazwyczaj tworzy lokalne wystąpienie tej klasy w funkcji [InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) jej obiektu aplikacji. Ten obiekt jest następnie przekazywany do [CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline), który wielokrotnie `CCommandLineInfo` wywołuje [ParseParam,](#parseparam) aby wypełnić obiekt. Obiekt `CCommandLineInfo` jest następnie przekazywany do [CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand) do obsługi argumentów wiersza polecenia i flagi.

Za pomocą tego obiektu można hermetyzować następujące opcje i parametry wiersza polecenia:

|Argument wiersza polecenia|Polecenie wykonane|
|----------------------------|----------------------|
|*App*|Nowy plik.|
|nazwa pliku *aplikacji*|Otwórz plik.|
|nazwa pliku *aplikacji* `/p`|Drukowanie pliku do drukarki domyślnej.|
|port sterownika drukarki nazwy pliku *aplikacji* `/pt`|Drukowanie pliku na określonej drukarce.|
|*aplikacja*`/dde`|Uruchom i poczekaj na polecenie DDE.|
|*aplikacja*`/Automation`|Uruchom jako serwer automatyzacji OLE.|
|*aplikacja*`/Embedding`|Uruchom, aby edytować osadzony element OLE.|
|*aplikacja*`/Register`<br /><br /> *aplikacja*`/Regserver`|Informuje aplikację o wykonaniu wszelkich zadań rejestracyjnych.|
|*aplikacja*`/Unregister`<br /><br /> *aplikacja*`/Unregserver`|Informuje aplikację o wykonaniu wszelkich zadań związanych z niezwolnieniami.|

Wyprowadzić nową klasę `CCommandLineInfo` z do obsługi innych flag i wartości parametrów. Zastąpać [ParseParam](#parseparam) do obsługi nowych flag.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CCommandLineInfo`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="ccommandlineinfoccommandlineinfo"></a><a name="ccommandlineinfo"></a>CCommandLineInfo::CCommandLineInfo

Konstruktor ten `CCommandLineInfo` tworzy obiekt z wartościami domyślnymi.

```
CCommandLineInfo();
```

### <a name="remarks"></a>Uwagi

Domyślnie jest to wyświetlenie `m_bShowSplash=TRUE`ekranu powitalnego ( ) i `m_nShellCommand`wykonanie polecenia Nowy w menu Plik ( **=NewFile**).

Struktura aplikacji wywołuje [ParseParam,](#parseparam) aby wypełnić elementy członkowskie danych tego obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#54](../../mfc/codesnippet/cpp/ccommandlineinfo-class_1.cpp)]

## <a name="ccommandlineinfom_brunautomated"></a><a name="m_brunautomated"></a>CCommandLineInfo::m_bRunAutomated

Wskazuje, że `/Automation` flaga została znaleziona w wierszu polecenia.

```
BOOL m_bRunAutomated;
```

### <a name="remarks"></a>Uwagi

Jeśli true, oznacza to uruchomienie jako serwer automatyzacji OLE.

## <a name="ccommandlineinfom_brunembedded"></a><a name="m_brunembedded"></a>CCommandLineInfo::m_bRunEmbedded

Wskazuje, że `/Embedding` flaga została znaleziona w wierszu polecenia.

```
BOOL m_bRunEmbedded;
```

### <a name="remarks"></a>Uwagi

Jeśli true, oznacza to uruchomienie do edycji osadzonego elementu OLE.

## <a name="ccommandlineinfom_bshowsplash"></a><a name="m_bshowsplash"></a>CCommandLineInfo::m_bShowSplash

Wskazuje, że ekran powitalny powinien być wyświetlany.

```
BOOL m_bShowSplash;
```

### <a name="remarks"></a>Uwagi

Jeśli true, oznacza to, że ekran powitalny dla tej aplikacji powinny być wyświetlane podczas uruchamiania. Domyślna implementacja [parseparam](#parseparam) ustawia ten element członkowski danych `CCommandLineInfo::FileNew`na WARTOŚĆ [TRUE,](#m_nshellcommand) jeśli m_nShellCommand jest równa .

## <a name="ccommandlineinfom_nshellcommand"></a><a name="m_nshellcommand"></a>CCommandLineInfo::m_nShellCommand

Wskazuje polecenie powłoki dla tego wystąpienia aplikacji.

```
m_nShellCommand;
```

### <a name="remarks"></a>Uwagi

Typ dla tego elementu członkowskiego danych jest następującym typem `CCommandLineInfo` wyliczonym, który jest zdefiniowany w klasie.

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

Aby uzyskać krótki opis tych wartości, zobacz poniższą listę.

- `CCommandLineInfo::FileNew`Wskazuje, że w wierszu polecenia nie znaleziono nazwy pliku.

- `CCommandLineInfo::FileOpen`Wskazuje, że w wierszu polecenia znaleziono nazwę pliku i że w wierszu `/p` `/pt`polecenia `/dde`nie znaleziono żadnej z następujących flag: , , .

- `CCommandLineInfo::FilePrint`Wskazuje, że `/p` flaga została znaleziona w wierszu polecenia.

- `CCommandLineInfo::FilePrintTo`Wskazuje, że `/pt` flaga została znaleziona w wierszu polecenia.

- `CCommandLineInfo::FileDDE`Wskazuje, że `/dde` flaga została znaleziona w wierszu polecenia.

- `CCommandLineInfo::AppRegister`Wskazuje, że `/Register` `/Regserver` lub flaga została znaleziona w wierszu polecenia i aplikacja została poproszona o rejestrację.

- `CCommandLineInfo::AppUnregister`Wskazuje, że `/Unregister` `/Unregserver` lub aplikacja została poproszona o wyrejestrowania.

- `CCommandLineInfo::RestartByRestartManager`Wskazuje, że aplikacja została ponownie uruchomiona przez menedżera ponownego uruchamiania.

- `CCommandLineInfo::FileNothing`Wyłącza wyświetlanie nowego okna podrzędnego MDI podczas uruchamiania. Zgodnie z projektem aplikacje MDI generowane przez Kreatora aplikacji wyświetlają nowe okno podrzędne podczas uruchamiania. Aby wyłączyć tę funkcję, aplikacja `CCommandLineInfo::FileNothing` może używać jako polecenia powłoki, gdy wywołuje [ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand). `ProcessShellCommand`jest wywoływana `InitInstance( )` przez `CWinApp` wszystkie klasy pochodne.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#55](../../mfc/codesnippet/cpp/ccommandlineinfo-class_2.cpp)]

## <a name="ccommandlineinfom_strdrivername"></a><a name="m_strdrivername"></a>CCommandLineInfo::m_strDriverName

Przechowuje wartość trzeciego parametru niebędącego flagą w wierszu polecenia.

```
CString m_strDriverName;
```

### <a name="remarks"></a>Uwagi

Ten parametr jest zazwyczaj nazwą sterownika drukarki dla polecenia Powłoka Drukuj na. Domyślna implementacja [ParseParam](#parseparam) ustawia ten `/pt` element członkowski danych tylko wtedy, gdy flaga została znaleziona w wierszu polecenia.

## <a name="ccommandlineinfom_strfilename"></a><a name="m_strfilename"></a>CCommandLineInfo::m_strFileName

Przechowuje wartość pierwszego parametru niebędącego flagą w wierszu polecenia.

```
CString m_strFileName;
```

### <a name="remarks"></a>Uwagi

Ten parametr jest zazwyczaj nazwą pliku do otwarcia.

## <a name="ccommandlineinfom_strportname"></a><a name="m_strportname"></a>CCommandLineInfo::m_strPortName

Przechowuje wartość czwartego parametru niebędącego flagą w wierszu polecenia.

```
CString m_strPortName;
```

### <a name="remarks"></a>Uwagi

Ten parametr jest zazwyczaj nazwą portu drukarki dla polecenia Powłoka Drukuj na. Domyślna implementacja [ParseParam](#parseparam) ustawia ten `/pt` element członkowski danych tylko wtedy, gdy flaga została znaleziona w wierszu polecenia.

## <a name="ccommandlineinfom_strprintername"></a><a name="m_strprintername"></a>CCommandLineInfo::m_strPrinterName

Przechowuje wartość drugiego parametru niebędącego flagą w wierszu polecenia.

```
CString m_strPrinterName;
```

### <a name="remarks"></a>Uwagi

Ten parametr jest zazwyczaj nazwą drukarki dla polecenia Print To shell. Domyślna implementacja [ParseParam](#parseparam) ustawia ten `/pt` element członkowski danych tylko wtedy, gdy flaga została znaleziona w wierszu polecenia.

## <a name="ccommandlineinfom_strrestartidentifier"></a><a name="m_strrestartidentifier"></a>CCommandLineInfo::m_strRestartIdentifier

Unikatowy identyfikator ponownego uruchomienia w wierszu polecenia.

```
CString m_strRestartIdentifier;
```

### <a name="remarks"></a>Uwagi

Identyfikator ponownego uruchomienia jest unikatowy dla każdego wystąpienia aplikacji.

Jeśli menedżer ponownego uruchamiania zakończy działanie aplikacji i jest skonfigurowany do jej ponownego uruchomienia, menedżer ponownego uruchamiania wykonuje aplikację z wiersza polecenia z identyfikatorem ponownego uruchomienia jako parametr opcjonalny. Gdy menedżer ponownego uruchamiania używa identyfikatora ponownego uruchamiania, aplikacja może ponownie otworzyć wcześniej otwarte dokumenty i odzyskać automatycznie uratowane pliki.

## <a name="ccommandlineinfoparseparam"></a><a name="parseparam"></a>CCommandLineInfo::ParseParam

Struktura wywołuje tę funkcję do analizowania/interpretowania poszczególnych parametrów z wiersza polecenia. Druga wersja różni się od pierwszej tylko w projektach Unicode.

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
Parametr lub flaga.

*bGłażej*<br/>
Wskazuje, czy *pszParam* jest parametrem, czy flagą.

*Blast*<br/>
Wskazuje, czy jest to ostatni parametr lub flaga w wierszu polecenia.

### <a name="remarks"></a>Uwagi

[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline) wywołuje `ParseParam` raz dla każdego parametru lub flagi w wierszu polecenia, przekazując argument do *pszParam*. Jeśli pierwszy znak parametru to **-**' ' **/** lub a ' ', zostanie on usunięty, a *bFlag* jest ustawiony na WARTOŚĆ TRUE. Podczas analizowania parametru końcowego *bStato* jest ustawione na WARTOŚĆ TRUE.

Domyślna implementacja tej funkcji rozpoznaje `/p` `/pt`następujące `/dde` `/Automation`flagi: `/Embedding`, , , i , jak pokazano w poniższej tabeli:

|Argument wiersza polecenia|Polecenie wykonane|
|----------------------------|----------------------|
|*App*|Nowy plik.|
|nazwa pliku *aplikacji*|Otwórz plik.|
|nazwa pliku *aplikacji* `/p`|Drukowanie pliku do drukarki domyślnej.|
|port sterownika drukarki nazwy pliku *aplikacji* `/pt`|Drukowanie pliku na określonej drukarce.|
|*aplikacja*`/dde`|Uruchom i poczekaj na polecenie DDE.|
|*aplikacja*`/Automation`|Uruchom jako serwer automatyzacji OLE.|
|*aplikacja*`/Embedding`|Uruchom, aby edytować osadzony element OLE.|
|*aplikacja*`/Register`<br /><br /> *aplikacja*`/Regserver`|Informuje aplikację o wykonaniu wszelkich zadań rejestracyjnych.|
|*aplikacja*`/Unregister`<br /><br /> *aplikacja*`/Unregserver`|Informuje aplikację o wykonaniu wszelkich zadań związanych z niezwolnieniami.|

Informacje te są przechowywane w [m_bRunAutomated,](#m_brunautomated) [m_bRunEmbedded](#m_brunembedded)i [m_nShellCommand.](#m_nshellcommand) Flagi są oznaczone ukośnikiem **/**" lub łącznikiem " ". **-**

Domyślna implementacja umieszcza pierwszy parametr niebędący flagą w [m_strFileName](#m_strfilename). W przypadku `/pt` flagi domyślna implementacja umieszcza odpowiednio parametry drugiego, trzeciego i czwartego parametru niebędącego flagą w [m_strPrinterName](#m_strprintername), [m_strDriverName](#m_strdrivername)i [m_strPortName.](#m_strportname)

Domyślna implementacja ustawia również [m_bShowSplash](#m_bshowsplash) true tylko w przypadku nowego pliku. W przypadku nowego pliku użytkownik podjął działania obejmujące samą aplikację. W każdym innym przypadku, w tym otwierania istniejących plików przy użyciu powłoki, akcja użytkownika obejmuje plik bezpośrednio. W punkcie widzenia zorientowanym na dokument ekran powitalny nie musi ogłaszać uruchamiania aplikacji.

Zastąpić tę funkcję w klasie pochodnej do obsługi innych wartości flagi i parametrów.

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)<br/>
[CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)
