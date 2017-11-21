---
title: Klasa CMFCEditBrowseCtrl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCEditBrowseCtrl
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableFileBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableFolderBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::GetMode
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnAfterUpdate
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnBrowse
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnChangeLayout
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnDrawBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnIllegalFileName
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::SetBrowseButtonImage
dev_langs: C++
helpviewer_keywords:
- CMFCEditBrowseCtrl [MFC], EnableBrowseButton
- CMFCEditBrowseCtrl [MFC], EnableFileBrowseButton
- CMFCEditBrowseCtrl [MFC], EnableFolderBrowseButton
- CMFCEditBrowseCtrl [MFC], GetMode
- CMFCEditBrowseCtrl [MFC], OnAfterUpdate
- CMFCEditBrowseCtrl [MFC], OnBrowse
- CMFCEditBrowseCtrl [MFC], OnChangeLayout
- CMFCEditBrowseCtrl [MFC], OnDrawBrowseButton
- CMFCEditBrowseCtrl [MFC], OnIllegalFileName
- CMFCEditBrowseCtrl [MFC], SetBrowseButtonImage
ms.assetid: 69cfd886-3d35-4bee-8901-7c88fcf9520f
caps.latest.revision: "33"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ceca13bd09483c788c430d420b53c88bb97ed34d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cmfceditbrowsectrl-class"></a>Klasa CMFCEditBrowseCtrl
`CMFCEditBrowseCtrl` Klasa obsługuje przeglądania edycji, znajduje się pole edycji tekstu, która opcjonalnie zawiera przycisk Przeglądaj. Gdy użytkownik kliknie przycisk Przeglądaj, formantu wykonuje akcję niestandardową lub wyświetla standardowe okno dialogowe zawiera przeglądarka plików lub folder przeglądarki.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCEditBrowseCtrl : public CEdit  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CMFCEditBrowseCtrl::CMFCEditBrowseCtrl`|Domyślny konstruktor.|  
|`CMFCEditBrowseCtrl::~CMFCEditBrowseCtrl`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton)|Włącza lub wyłącza (ukrywa) przycisk Przeglądaj.|  
|[CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)|Włącza przycisk Przeglądaj i umieszcza formancie edycyjnym przeglądania *przeglądania plików* tryb.|  
|[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)|Włącza przycisk Przeglądaj i umieszcza formancie edycyjnym przeglądania *przeglądania folderu* tryb.|  
|[CMFCEditBrowseCtrl::GetMode](#getmode)|Zwraca bieżący tryb przeglądania.|  
|[CMFCEditBrowseCtrl::OnAfterUpdate](#onafterupdate)|Wywoływane przez platformę po zaktualizowaniu przeglądania edycji wynikami akcji przeglądania.|  
|[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)|Wywoływane przez platformę, po kliknięciu przycisku Przeglądaj.|  
|[CMFCEditBrowseCtrl::OnChangeLayout](#onchangelayout)|Ponownie rysuje bieżącej edycji przeglądania.|  
|[CMFCEditBrowseCtrl::OnDrawBrowseButton](#ondrawbrowsebutton)|Wywoływane przez platformę, by narysować przycisk Przeglądaj.|  
|[CMFCEditBrowseCtrl::OnIllegalFileName](#onillegalfilename)|Wywoływane przez platformę, gdy w formancie edycyjnym Wprowadzono niedozwoloną nazwę pliku.|  
|`CMFCEditBrowseCtrl::PreTranslateMessage`|Wykonuje translację komunikaty okna przed wysłaniem do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) i [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkcje systemu Windows. Składnia i uzyskać więcej informacji, zobacz [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).|  
|[CMFCEditBrowseCtrl::SetBrowseButtonImage](#setbrowsebuttonimage)|Ustawia niestandardowego obrazu dla przycisku Przeglądaj.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj formantu edycyjnego Przeglądaj, aby wybrać nazwę pliku lub folderu. Opcjonalnie można użyć formantu do wykonywania akcji niestandardowej tak, aby wyświetlić okno dialogowe. Można wyświetlić lub nie być wyświetlany przycisk Przeglądaj i można zastosować etykiety niestandardowej lub obrazu przycisku.  
  
 *Tryb przeglądania* z przeglądania edycji kontroli określa, czy zawiera przycisk Przeglądaj i jaka akcja występuje po kliknięciu przycisku. Aby uzyskać więcej informacji, zobacz [GetMode](#getmode) metody.  
  
 `CMFCEditBrowseCtrl` Klasa obsługuje następujące tryby.  
  
 `custom mode`  
 Akcja niestandardowa jest wykonywane, gdy użytkownik kliknie przycisk Przeglądaj. Na przykład można wyświetlić okno dialogowe specyficzne dla aplikacji.  
  
 `file mode`  
 Okno dialogowe wyboru pliku jest wyświetlany, gdy użytkownik kliknie przycisk Przeglądaj.  
  
 `folder mode`  
 Okno dialogowe wybór folderu standard jest wyświetlany, gdy użytkownik kliknie przycisk Przeglądaj.  
  
## <a name="how-to-specify-an-edit-browse-control"></a>Instrukcje: Określanie formantu edycyjnego przeglądania  
 Wykonaj poniższe kroki, aby dołączyć do nich przeglądania edycji w aplikacji:  
  
1.  Jeśli chcesz wdrożyć tryb przeglądania niestandardowych, pochodzi z klasy z `CMFCEditBrowseCtrl` klasy, a następnie zastąpić [CMFCEditBrowseCtrl::OnBrowse](#onbrowse) metody. Przesłoniętej metody wykonać akcji niestandardowej przeglądania i zaktualizuj przeglądania kontrolki edycji z wynikiem.  
  
2.  Osadź albo `CMFCEditBrowseCtrl` obiektu lub edycji pochodnej przeglądania sterowania do obiektu okna nadrzędnego.  
  
3.  Jeśli używasz **Kreator klas** Aby utworzyć okno dialogowe, Dodaj formant edycyjny ( `CEdit`) do formularz okna dialogowego. Ponadto Dodaj zmienną do kontroli dostępu w pliku nagłówka. W pliku nagłówka, Zmień typ zmiennej z `CEdit` do `CMFCEditBrowseCtrl`. Przeglądaj edycji zostaną utworzone automatycznie. Jeśli nie używasz **Kreator klas**, Dodaj `CMFCEditBrowseCtrl` zmienną do pliku nagłówka, a następnie wywołania jego `Create` metody.  
  
4.  Jeśli dodasz formant edycyjny przejdź do okna dialogowego, użyj **ClassWizard** narzędzia do konfigurowania wymiany danych.  
  
5.  Wywołanie [EnableFolderBrowseButton](#enablefolderbrowsebutton), [EnableFileBrowseButton](#enablefilebrowsebutton), lub [EnableBrowseButton](#enablebrowsebutton) metodę, aby ustawić tryb przeglądania i wyświetlić przycisk Przeglądaj. Wywołanie [GetMode](#getmode) metodę, aby uzyskać bieżący tryb przeglądania.  
  
6.  Aby zapewnić niestandardowego obrazu dla przycisku przeglądania, należy wywołać [SetBrowseButtonImage](#setbrowsebuttonimage) metody lub zastąpienie [OnDrawBrowseButton](#ondrawbrowsebutton) metody.  
  
7.  Aby usunąć przycisk przeglądania kontrolki edycji przeglądania, wywołaj [EnableBrowseButton](#enablebrowsebutton) metody z `bEnable` ustawiono parametr `FALSE`.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak używać dwóch metod w `CMFCEditBrowseCtrl` klasy: `EnableFolderBrowseButton` i `EnableFileBrowseButton`. Ten przykład jest częścią [próbki nowe formanty](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxeditbrowsectrl.h  
  
##  <a name="enablebrowsebutton"></a>CMFCEditBrowseCtrl::EnableBrowseButton  
 Wyświetla lub nie jest wyświetlany przycisk przeglądania na bieżącej edycji przeglądania.  
  
```  
void EnableBrowseButton(
    BOOL bEnable=TRUE,  
    LPCTSTR szLabel=_T("..."));
```  
  
### <a name="parameters"></a>Parametry  
 `bEnable`  
 `TRUE`Aby wyświetlić przycisk przeglądania; `FALSE` nie, aby wyświetlić przycisk Przeglądaj. Wartość domyślna to `TRUE`.  
  
 `szLabel`  
 Etykiety, który jest wyświetlany na przycisku Przeglądaj. Wartość domyślna to " **...** ".  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `bEnable` parametr jest `TRUE`, wykonania niestandardowej akcji do wykonania po kliknięciu przycisku Przeglądaj. Do wykonania akcji niestandardowej, klasa wyprowadzona z `CMFCEditBrowseCtrl` klasy, a następnie zastąpić jej [OnBrowse](#onbrowse) metody.  
  
 Jeśli `bEnable` parametr jest `TRUE`, jest w trybie przeglądania kontrolki `BrowseMode_Default`; w przeciwnym razie tryb przeglądania jest `BrowseMode_None`. Aby uzyskać więcej informacji na temat trybów przeglądania, zobacz [GetMode](#getmode) metody.  
  
##  <a name="enablefilebrowsebutton"></a>CMFCEditBrowseCtrl::EnableFileBrowseButton  
 Przedstawia przycisk przeglądania na bieżącej edycji przeglądania i daje kontrolę *przeglądania plików* tryb.  
  
```  
void EnableFileBrowseButton(
    LPCTSTR lpszDefExt=NULL,  
    LPCTSTR lpszFilter=NULL,  
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszDefExt`  
 Określa domyślne rozszerzenie nazwy pliku używanego w oknie dialogowym Wybieranie pliku. Wartość domyślna to `NULL`.  
  
 `lpszFilter`  
 Określa domyślny ciąg filtru jest używana w oknie dialogowym Wybieranie pliku. Wartość domyślna to `NULL`.  
  
 `dwFlags`  
 Flagi — okno dialogowe. Wartość domyślna to bitowe połączenie (lub) OFN_HIDEREADONLY i OFN_OVERWRITEPROMPT.  
  
### <a name="remarks"></a>Uwagi  
 Podczas przeglądania edycji jest w trybie przeglądania plików, a użytkownik kliknie przycisk przeglądania, kontrolka Wyświetla okna dialogowego wyboru pliku.  
  
 Aby uzyskać pełną listę dostępnych flag, zobacz [struktury OPENFILENAME](https://msdn.microsoft.com/library/ms646839.aspx).  
  
##  <a name="enablefolderbrowsebutton"></a>CMFCEditBrowseCtrl::EnableFolderBrowseButton  
 Przedstawia przycisk przeglądania na bieżącej edycji przeglądania i daje kontrolę *przeglądania folderu* tryb.  
  
```  
void EnableFolderBrowseButton();
```  
  
### <a name="remarks"></a>Uwagi  
 Podczas przeglądania edycji jest w trybie przeglądania folderów, a użytkownik kliknie przycisk przeglądania, kontrolka Wyświetla okno dialogowe wybór folderu standard.  
  
##  <a name="getmode"></a>CMFCEditBrowseCtrl::GetMode  
 Pobiera tryb przeglądania bieżącego przeglądania kontrolki edycji.  
  
```  
CMFCEditBrowseCtrl::BrowseMode GetMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jedną z wartości wyliczenia, które określa bieżący tryb edycji Przeglądaj formantu. Tryb przeglądania Określa, czy w ramach Wyświetla przycisk Przeglądaj i akcję występuje po kliknięciu tego przycisku.  
  
 W poniższej tabeli przedstawiono możliwe wartości zwracane.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`BrowseMode_Default`|`custom mode`. Zdefiniowane przez programistę czynności.|  
|`BrowseMode_File`|`file mode`. Zostanie wyświetlone okno dialogowe przeglądarki standardowego pliku.|  
|`BrowseMode_Folder`|`folder mode`. Zostanie wyświetlone okno dialogowe przeglądarki folderu standard.|  
|`BrowseMode_None`|Przycisk przeglądania nie jest wyświetlana.|  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie `CMFCEditBrowseCtrl` obiektu jest ustawiana na `BrowseMode_None` tryb. Tryb przeglądania z zmodyfikować [CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton), [CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton), i [CMFCEditBrowseCtrl::EnableFolderBrowseButton ](#enablefolderbrowsebutton) metody.  
  
##  <a name="onafterupdate"></a>CMFCEditBrowseCtrl::OnAfterUpdate  
 Wywoływane przez platformę po zaktualizowaniu przeglądania edycji wynikami akcji przeglądania.  
  
```  
virtual void OnAfterUpdate();
```  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę w klasie pochodnej w celu wykonania akcji niestandardowej.  
  
##  <a name="onbrowse"></a>CMFCEditBrowseCtrl::OnBrowse  
 Wywoływane przez platformę, po kliknięciu przycisku przeglądania kontrolki edycji przeglądania.  
  
```  
virtual void OnBrowse();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia wykonanie kodu niestandardowego, po kliknięciu przycisku przeglądania kontrolki edycji przeglądania. Pochodzi z klasy z `CMFCEditBrowseCtrl` klasy i zastąp jego `OnBrowse` metody. W tej metodzie wykonania akcji niestandardowej przeglądania i opcjonalnie zaktualizuj pola tekstowego kontrolki edycji przeglądania. W aplikacji, użyj [EnableBrowseButton](#enablebrowsebutton) metody, które mają zostać umieszczone w formancie edycyjnym przeglądania *Przeglądaj niestandardowe* tryb.  
  
##  <a name="onchangelayout"></a>CMFCEditBrowseCtrl::OnChangeLayout  
 Ponownie rysuje bieżącej edycji przeglądania.  
  
```  
virtual void OnChangeLayout();
```  
  
### <a name="remarks"></a>Uwagi  
 Platformę wywołuje tę metodę, gdy tryb przeglądania Przeglądaj edycji kontroli zmian. Aby uzyskać więcej informacji, zobacz [CMFCEditBrowseCtrl::GetMode](#getmode).  
  
##  <a name="ondrawbrowsebutton"></a>CMFCEditBrowseCtrl::OnDrawBrowseButton  
 Wywoływane przez platformę, by narysować przycisk przeglądania w formancie edycyjnym przeglądania.  
  
```  
virtual void OnDrawBrowseButton(
    CDC* pDC,  
    CRect rect,  
    BOOL bIsButtonPressed,  
    BOOL bIsButtonHot);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 `Rect`  
 Prostokąt ograniczający przycisk Przeglądaj.  
  
 `bIsButtonPressed`  
 `TRUE`Jeśli przycisk jest naciśnięty; w przeciwnym razie `FALSE`.  
  
 `bIsButtonHot`  
 `TRUE`Jeśli przycisk jest wyróżniony; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę funkcję w klasie pochodnej, aby dostosować wygląd przycisku Przeglądaj.  
  
##  <a name="setbrowsebuttonimage"></a>CMFCEditBrowseCtrl::SetBrowseButtonImage  
 Ustawia obraz niestandardowy przycisku przeglądania kontrolki edycji przeglądania.  
  
```  
void SetBrowseButtonImage(
    HICON hIcon,  
    BOOL bAutoDestroy= TRUE);

 
void SetBrowseButtonImage(
    HBITMAP hBitmap,  
    BOOL bAutoDestroy= TRUE);  
  
void SetBrowseButtonImage(UINT uiBmpResId);
```  
  
### <a name="parameters"></a>Parametry  
 `hIcon`  
 Dojście ikony.  
  
 `hBitmap`  
 Dojście mapy bitowej.  
  
 `uiBmpResId`  
 Identyfikator zasobu mapy bitowej.  
  
 `bAutoDestroy`  
 `TRUE`Aby usunąć określony ikony lub mapy bitowej, gdy ta metoda jest kończona; w przeciwnym razie `FALSE`. Wartość domyślna to `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby zastosować niestandardowy obraz do przycisku przeglądania. Domyślnie platformę uzyskuje standardowy obraz, gdy formant edycyjny przeglądania jest w *przeglądania plików* lub *przeglądania folderu* tryb.  
  
##  <a name="onillegalfilename"></a>CMFCEditBrowseCtrl::OnIllegalFileName  
 Wywoływane przez platformę, gdy w formancie edycyjnym Wprowadzono niedozwoloną nazwę pliku.  
  
```  
virtual BOOL OnIllegalFileName(CString& strFileName);
```  
  
### <a name="parameters"></a>Parametry  
 `strFileName`  
 Określa nazwę pliku niedozwolona.  
  
### <a name="return-value"></a>Wartość zwracana  
 Należy zwrócić `FALSE` Jeśli ta nazwa pliku nie można przekazywać w przypadku okna dialogowego pliku. W takim przypadku fokus jest ustawiana dla kontrolki edycji i edytowanie użytkownika powinno być kontynuowane. Domyślna implementacja wyświetla komunikat informujący użytkownika o niedozwoloną nazwę pliku i zwraca `FALSE`. Należy przesłonić tę metodę, Popraw nazwę pliku i zwracać `TRUE` dla dalszego przetwarzania.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)
