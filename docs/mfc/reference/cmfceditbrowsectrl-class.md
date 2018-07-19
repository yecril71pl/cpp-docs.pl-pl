---
title: Klasa CMFCEditBrowseCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d00488a7e9a87116317aec35c82b73b40077d8c
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37854011"
---
# <a name="cmfceditbrowsectrl-class"></a>Klasa CMFCEditBrowseCtrl
`CMFCEditBrowseCtrl` Klasa obsługuje formant przeglądania edycji, który jest edytowalnym polem tekstowym opcjonalnie zawierający przycisk przeglądania. Gdy użytkownik kliknie przycisk przeglądania, formant wykonuje niestandardowe lub wyświetla standardowe okno dialogowe zawierający przeglądarkę plików lub przeglądarkę katalogów.  
  
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
|[CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton)|Włącza lub wyłącza (ukrywa) przycisk przeglądania.|  
|[CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)|Włącza przycisk Przeglądaj i umieszcza formant przeglądania edycji w *przeglądanie plików* trybu.|  
|[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)|Włącza przycisk Przeglądaj i umieszcza formant przeglądania edycji w *przeglądanie folderów* trybu.|  
|[CMFCEditBrowseCtrl::GetMode](#getmode)|Zwraca bieżący tryb przeglądania.|  
|[CMFCEditBrowseCtrl::OnAfterUpdate](#onafterupdate)|Wywoływane przez platformę, po zaktualizowaniu formant przeglądania edycji z wynikami akcji przeglądania.|  
|[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)|Wywoływane przez platformę po użytkownik kliknie przycisk przeglądania.|  
|[CMFCEditBrowseCtrl::OnChangeLayout](#onchangelayout)|Odrysowuje bieżącego formant przeglądania edycji.|  
|[CMFCEditBrowseCtrl::OnDrawBrowseButton](#ondrawbrowsebutton)|Metoda wywoływana przez platformę, by narysować przycisk przeglądania.|  
|[CMFCEditBrowseCtrl::OnIllegalFileName](#onillegalfilename)|Wywoływane przez platformę, gdy wprowadzono niedozwoloną nazwę pliku w formancie edycji.|  
|`CMFCEditBrowseCtrl::PreTranslateMessage`|Wykonuje translację komunikatów okien, zanim zostaną rozesłane do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) i [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkcje Windows. Informacje o składni i więcej informacji, zobacz [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).|  
|[CMFCEditBrowseCtrl::SetBrowseButtonImage](#setbrowsebuttonimage)|Ustawia niestandardowy obraz dla przycisku Przeglądaj.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj formant przeglądania edycji, aby wybrać nazwę pliku lub folderu. Opcjonalnie za pomocą kontrolki wykonywanie niestandardowej akcji, takich jak, aby wyświetlić okno dialogowe. Możesz wyświetlać lub przycisk przeglądania nie jest wyświetlany i stosować etykiety niestandardowej lub obrazu na przycisku.  
  
 *Tryb przeglądania* przeglądania edycji kontrolki Określa czy Wyświetla przycisk przeglądania i jakie działania pojawia się po kliknięciu przycisku. Aby uzyskać więcej informacji, zobacz [GetMode](#getmode) metody.  
  
 `CMFCEditBrowseCtrl` Klasa obsługuje następujące tryby.  
  
 **Tryb niestandardowy**  
 Akcja niestandardowa jest wykonywane, gdy użytkownik kliknie przycisk przeglądania. Na przykład można wyświetlić okno dialogowe specyficzne dla aplikacji.  
  
 **tryb pliku**  
 Okno dialogowe Wybieranie standardowych plików jest wyświetlana, gdy użytkownik kliknie przycisk przeglądania.  
  
 **Tryb folderu**  
 Okno dialogowe Wybieranie folderu standard jest wyświetlany, gdy użytkownik kliknie przycisk przeglądania.  
  
## <a name="how-to-specify-an-edit-browse-control"></a>Instrukcje: Określanie formant przeglądania edycji  
 Wykonaj poniższe kroki, aby włączyć formant przeglądania edycji w Twojej aplikacji:  
  
1.  Jeśli chcesz zaimplementować tryb przeglądanie niestandardowe pochodną klasy z `CMFCEditBrowseCtrl` klasy, a następnie zastąpić [CMFCEditBrowseCtrl::OnBrowse](#onbrowse) metody. W metodzie zgodnym z przesłoniętą wykonać akcji niestandardowej przeglądania i zaktualizuj formant przeglądania edycji z wynikiem.  
  
2.  Osadzanie albo `CMFCEditBrowseCtrl` obiekt lub obiekt formant przeglądania edycji pochodnej do okna nadrzędnego obiektu.  
  
3.  Jeśli używasz **Kreator klas** Aby utworzyć okno dialogowe, należy dodać formant edycji ( `CEdit`) do formularza okno dialogowe. Ponadto można dodać zmiennej, aby uzyskać dostęp do formantu w pliku nagłówka. W pliku nagłówka, Zmień typ zmiennej z `CEdit` do `CMFCEditBrowseCtrl`. Formant przeglądania edycji zostaną utworzone automatycznie. Jeśli nie używasz **Kreator klas**, Dodaj `CMFCEditBrowseCtrl` zmiennej do pliku nagłówka i następnie wywołaniu jego `Create` metody.  
  
4.  Jeśli dodasz formant przeglądania edycji do okna dialogowego, użyj **ClassWizard** narzędzie, aby skonfigurować wymiany danych.  
  
5.  Wywołaj [EnableFolderBrowseButton](#enablefolderbrowsebutton), [EnableFileBrowseButton](#enablefilebrowsebutton), lub [enablebrowsebutton —](#enablebrowsebutton) metodę, aby ustawić tryb przeglądania i wyświetlić przycisk przeglądania. Wywołaj [GetMode](#getmode) metodę, aby uzyskać bieżący tryb przeglądania.  
  
6.  Aby zapewnić obraz niestandardowy przycisk przeglądania, należy wywołać [SetBrowseButtonImage](#setbrowsebuttonimage) metody lub zastąpienie [OnDrawBrowseButton](#ondrawbrowsebutton) metody.  
  
7.  Aby usunąć formant przeglądania edycji przycisk przeglądania, należy wywołać [enablebrowsebutton —](#enablebrowsebutton) metody z *bWłączenie* parametr jest ustawiony na wartość FALSE.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak istnieją dwie metody w `CMFCEditBrowseCtrl` klasy: `EnableFolderBrowseButton` i `EnableFileBrowseButton`. W tym przykładzie jest częścią [przykładowe nowych formantów](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxeditbrowsectrl.h  
  
##  <a name="enablebrowsebutton"></a>  CMFCEditBrowseCtrl::EnableBrowseButton  
 Wyświetla lub nie jest wyświetlany przycisk przeglądania na bieżącym formant przeglądania edycji.  
  
```  
void EnableBrowseButton(
    BOOL bEnable=TRUE,  
    LPCTSTR szLabel=_T("..."));
```  
  
### <a name="parameters"></a>Parametry  
 *bWłączenie*  
 Wartość TRUE, aby wyświetlić przycisk przeglądania; FALSE, aby nie wyświetlać przycisk przeglądania. Wartość domyślna to TRUE.  
  
 *szLabel*  
 Etykieta, który jest wyświetlany na przycisku Przeglądaj. Wartość domyślna to " **...** ".  
  
### <a name="remarks"></a>Uwagi  
 Jeśli *bWłączenie* parametr ma wartość PRAWDA, implementować akcję niestandardową do wykonania, gdy kliknięto przycisk przeglądania. Aby zaimplementować akcję niestandardową, należy wyprowadzić klasę z `CMFCEditBrowseCtrl` klasy, a następnie zastąpić jej [onbrowse —](#onbrowse) metody.  
  
 Jeśli *bWłączenie* parametr ma wartość PRAWDA, to tryb przeglądania kontrolki `BrowseMode_Default`; w przeciwnym razie tryb przeglądania jest `BrowseMode_None`. Aby uzyskać więcej informacji na temat trybów przeglądania, zobacz [GetMode](#getmode) metody.  
  
##  <a name="enablefilebrowsebutton"></a>  CMFCEditBrowseCtrl::EnableFileBrowseButton  
 Wyświetla przycisk przeglądania na bieżącym formant przeglądania edycji i umieszcza formantu *przeglądanie plików* trybu.  
  
```  
void EnableFileBrowseButton(
    LPCTSTR lpszDefExt=NULL,  
    LPCTSTR lpszFilter=NULL,  
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszDefExt*  
 Określa rozszerzenie nazwy pliku domyślny, który jest używany w oknie dialogowym wyboru plików. Wartością domyślną jest NULL.  
  
 *lpszFilter*  
 Określa domyślny ciąg filtru jest używana w oknie dialogowym wyboru plików. Wartością domyślną jest NULL.  
  
 *Flagidw*  
 Flagi okno dialogowe. Wartością domyślną jest bitową kombinacją (lub) OFN_HIDEREADONLY i OFN_OVERWRITEPROMPT.  
  
### <a name="remarks"></a>Uwagi  
 Gdy formant przeglądania edycji jest w trybie przeglądania plików, a użytkownik kliknie przycisk przeglądania, formant Wyświetla okno dialogowe Wybieranie standardowych plików.  
  
 Aby uzyskać pełną listę dostępnych flag, zobacz [LPSTRFILE struktury openfilename](https://msdn.microsoft.com/library/ms646839.aspx).  
  
##  <a name="enablefolderbrowsebutton"></a>  CMFCEditBrowseCtrl::EnableFolderBrowseButton  
 Wyświetla przycisk przeglądania na bieżącym formant przeglądania edycji i umieszcza formantu *przeglądanie folderów* trybu.  
  
```  
void EnableFolderBrowseButton();
```  
  
### <a name="remarks"></a>Uwagi  
 Gdy formant przeglądania edycji jest w trybie przeglądania folderów, a użytkownik kliknie przycisk przeglądania, formant Wyświetla okno dialogowe wyboru folderu standard.  
  
##  <a name="getmode"></a>  CMFCEditBrowseCtrl::GetMode  
 Pobiera tryb przeglądania bieżącego formant przeglądania edycji.  
  
```  
CMFCEditBrowseCtrl::BrowseMode GetMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Przejdź jedną z wartości wyliczenia, które określa bieżący tryb edycji kontrolki. Tryb przeglądania Określa, czy w ramach Wyświetla przycisk przeglądania i jaka akcja występuje, gdy użytkownik kliknie ten przycisk.  
  
 Poniższa tabela zawiera listę możliwych wartości zwracanych.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`BrowseMode_Default`|**trybu niestandardowego**. Odbywa się to działanie zdefiniowane przez programistę.|  
|`BrowseMode_File`|**tryb pliku**. Zostanie wyświetlone okno dialogowe przeglądarki standardowego pliku.|  
|`BrowseMode_Folder`|**Tryb folderu**. Zostanie wyświetlone okno dialogowe przeglądarki folderu standard.|  
|`BrowseMode_None`|Przycisk przeglądania nie jest wyświetlana.|  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie `CMFCEditBrowseCtrl` obiekt jest inicjowany do `BrowseMode_None` trybu. Modyfikowanie tryb przeglądania z [CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton), [CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton), i [CMFCEditBrowseCtrl::EnableFolderBrowseButton ](#enablefolderbrowsebutton) metody.  
  
##  <a name="onafterupdate"></a>  CMFCEditBrowseCtrl::OnAfterUpdate  
 Wywoływane przez platformę, po zaktualizowaniu formant przeglądania edycji z wynikami akcji przeglądania.  
  
```  
virtual void OnAfterUpdate();
```  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę w klasie pochodnej w celu wykonania akcji niestandardowej.  
  
##  <a name="onbrowse"></a>  CMFCEditBrowseCtrl::OnBrowse  
 Wywoływane przez platformę, po kliknięciu przycisku przeglądania formant przeglądania edycji.  
  
```  
virtual void OnBrowse();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia wykonanie kodu niestandardowego, gdy użytkownik kliknie przycisk przeglądania formant przeglądania edycji. Pochodną klasy z `CMFCEditBrowseCtrl` klasy i zastąp jego `OnBrowse` metody. W tej metodzie wykonania akcji niestandardowej przeglądania i opcjonalnie zaktualizuj pole tekstowe formant przeglądania edycji. W aplikacji, należy użyć [enablebrowsebutton —](#enablebrowsebutton) metodę, aby umieścić formant przeglądania edycji w *przeglądanie niestandardowe* trybu.  
  
##  <a name="onchangelayout"></a>  CMFCEditBrowseCtrl::OnChangeLayout  
 Odrysowuje bieżącego formant przeglądania edycji.  
  
```  
virtual void OnChangeLayout();
```  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tę metodę, gdy tryb przeglądania przeglądania edycji kontrolować zmiany. Aby uzyskać więcej informacji, zobacz [CMFCEditBrowseCtrl::GetMode](#getmode).  
  
##  <a name="ondrawbrowsebutton"></a>  CMFCEditBrowseCtrl::OnDrawBrowseButton  
 Metoda wywoływana przez platformę, by narysować przycisk przeglądania na formant przeglądania edycji.  
  
```  
virtual void OnDrawBrowseButton(
    CDC* pDC,  
    CRect rect,  
    BOOL bIsButtonPressed,  
    BOOL bIsButtonHot);
```  
  
### <a name="parameters"></a>Parametry  
 *podstawowego kontrolera domeny*  
 Wskaźnik do kontekstu urządzenia.  
  
 *Rect*  
 Prostokąt otaczający przycisk przeglądania.  
  
 *bIsButtonPressed*  
 Wartość TRUE, jeśli przycisk jest wciśnięty; w przeciwnym razie wartość FALSE.  
  
 *bIsButtonHot*  
 Wartość TRUE, jeśli przycisk jest wyróżniony; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę funkcję w klasie pochodnej, aby dostosować wygląd przycisk przeglądania.  
  
##  <a name="setbrowsebuttonimage"></a>  CMFCEditBrowseCtrl::SetBrowseButtonImage  
 Ustawia obraz niestandardowy na przycisku przeglądania formant przeglądania edycji.  
  
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
 *hIcon*  
 Uchwyt ikony.  
  
 *hBitmap*  
 Uchwyt mapy bitowej.  
  
 *uiBmpResId*  
 Identyfikator zasobu mapy bitowej.  
  
 *bAutoDestroy*  
 Wartość TRUE, aby usunąć określony ikona lub mapa bitowa, gdy ta metoda kończy działanie; w przeciwnym razie wartość FALSE. Wartość domyślna to TRUE.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia zastosowanie obrazu niestandardowego do przycisku przeglądania. Domyślnie struktura uzyskuje standardowy obraz, gdy formant przeglądania edycji znajduje się w *przeglądanie plików* lub *przeglądanie folderów* trybu.  
  
##  <a name="onillegalfilename"></a>  CMFCEditBrowseCtrl::OnIllegalFileName  
 Wywoływane przez platformę, gdy wprowadzono niedozwoloną nazwę pliku w formancie edycji.  
  
```  
virtual BOOL OnIllegalFileName(CString& strFileName);
```  
  
### <a name="parameters"></a>Parametry  
 *strFileName*  
 Określa nazwę pliku niedozwolone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Powinna zwrócić FALSE, jeśli ta nazwa pliku nie może być przekazywany dostosowaną okno dialogowe pliku. W tym przypadku fokus jest ustawiana dla kontrolki edycji, a użytkownik powinien kontynuować edycję. Domyślna implementacja Wyświetla okno komunikatu z informacją dla użytkownika o nazwie pliku niedozwolone i zwraca wartość FALSE. Należy przesłonić tę metodę, Popraw nazwę pliku i zwraca wartość TRUE, do dalszego przetwarzania.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)
