---
title: Klasa CMFCToolBarDateTimeCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CanBeStretched
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CopyFrom
- AFXTOOLBARDATETIMECTRL/CMFCToolBarButton::ExportToMenuButton
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetByCmd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetHwnd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetTime
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetTimeAll
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::HaveHotBorder
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::NotifyCommand
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnAddToCustomizePage
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnChangeParentWnd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnClick
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnCtlColor
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnMove
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnShow
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnUpdateToolTip
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::SetTime
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::SetTimeAll
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarDateTimeCtrl [MFC], CMFCToolBarDateTimeCtrl
- CMFCToolBarDateTimeCtrl [MFC], CanBeStretched
- CMFCToolBarDateTimeCtrl [MFC], CopyFrom
- CMFCToolBarButton [MFC], ExportToMenuButton
- CMFCToolBarDateTimeCtrl [MFC], GetByCmd
- CMFCToolBarDateTimeCtrl [MFC], GetDateTimeCtrl
- CMFCToolBarDateTimeCtrl [MFC], GetHwnd
- CMFCToolBarDateTimeCtrl [MFC], GetTime
- CMFCToolBarDateTimeCtrl [MFC], GetTimeAll
- CMFCToolBarDateTimeCtrl [MFC], HaveHotBorder
- CMFCToolBarDateTimeCtrl [MFC], NotifyCommand
- CMFCToolBarDateTimeCtrl [MFC], OnAddToCustomizePage
- CMFCToolBarDateTimeCtrl [MFC], OnChangeParentWnd
- CMFCToolBarDateTimeCtrl [MFC], OnClick
- CMFCToolBarDateTimeCtrl [MFC], OnCtlColor
- CMFCToolBarDateTimeCtrl [MFC], OnGlobalFontsChanged
- CMFCToolBarDateTimeCtrl [MFC], OnMove
- CMFCToolBarDateTimeCtrl [MFC], OnShow
- CMFCToolBarDateTimeCtrl [MFC], OnUpdateToolTip
- CMFCToolBarDateTimeCtrl [MFC], SetTime
- CMFCToolBarDateTimeCtrl [MFC], SetTimeAll
ms.assetid: a3853cb9-8ebc-444f-a1e4-9cf905e24c18
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 31bf2796d85dec335183b61a83ea5c675d5f4602
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038949"
---
# <a name="cmfctoolbardatetimectrl-class"></a>Klasa CMFCToolBarDateTimeCtrl
Przycisk paska narzędzi, który zawiera formant selektora daty i godziny.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl](#cmfctoolbardatetimectrl)|Konstruuje `CMFCToolBarDateTimeCtrl` obiektu.|  
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCToolBarDateTimeCtrl::CanBeStretched](#canbestretched)|Określa, czy użytkownik może stretch przycisku w trakcie dostosowywania realizowanego. (Przesłania [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|  
|[CMFCToolBarDateTimeCtrl::CopyFrom](#copyfrom)|Kopiuje właściwości inny przycisk paska narzędzi do bieżącego przycisku. (Przesłania [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|  
|`CMFCToolBarDateTimeCtrl::DuplicateData`|Zarezerwowane do użytku w przyszłości.|  
|[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|Kopiuje tekst przycisku paska narzędzi do menu.|  
|`CMFCToolBarDateTimeCtrl::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|[CMFCToolBarDateTimeCtrl::GetByCmd](#getbycmd)|Pobiera pierwszy `CMFCToolBarDateTimeCtrl` obiektu w aplikacji, która ma identyfikator określonego polecenia.|  
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](#getdatetimectrl)|Zwraca wskaźnik do formant wyboru daty i godziny.|  
|[CMFCToolBarDateTimeCtrl::GetHwnd](#gethwnd)|Pobiera uchwytu okna, który jest skojarzony z przycisku paska narzędzi. (Przesłania [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|  
|`CMFCToolBarDateTimeCtrl::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|[CMFCToolBarDateTimeCtrl::GetTime](#gettime)|Pobiera zaznaczony czas z formant wyboru daty i godziny i umieszczenie go w określonym [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktury.|  
|[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)|Zwraca zaznaczony czas przycisku formantu selektora czas, który ma identyfikator określonego polecenia.|  
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](#havehotborder)|Określa, czy obramowania przycisku jest wyświetlany, gdy użytkownik wybierze przycisk. (Przesłania [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|  
|[CMFCToolBarDateTimeCtrl::NotifyCommand](#notifycommand)|Określa, czy przycisk przetwarza [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) wiadomości. (Przesłania [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|  
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](#onaddtocustomizepage)|Wywoływane przez platformę, gdy przycisk zostanie dodany do **Dostosuj** okno dialogowe. (Przesłania [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|  
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|Wywoływane przez platformę, by Oblicz rozmiar przycisku dla kontekstu określonego urządzenia i stan dokowania. (Przesłania [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|  
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](#onchangeparentwnd)|Wywoływane przez platformę, gdy przycisk jest wstawiany do nowego paska narzędzi. (Przesłania [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|  
|[CMFCToolBarDateTimeCtrl::OnClick](#onclick)|Wywoływane przez platformę, gdy użytkownik kliknie formantu. (Przesłania [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|  
|[CMFCToolBarDateTimeCtrl::OnCtlColor](#onctlcolor)|Wywoływane przez platformę, obsługując narzędzi nadrzędnej wm_ctlcolor — komunikat. (Przesłania [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|  
|`CMFCToolBarDateTimeCtrl::OnDraw`|Wywoływane przez platformę, by narysować przycisku przy użyciu określonych stylów i opcje. (Przesłania [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|  
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|Wywoływane przez platformę, by narysować przycisku **polecenia** okienku **Dostosuj** okno dialogowe. (Przesłania [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|  
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](#onglobalfontschanged)|Wywoływane przez platformę, gdy globalne czcionka została zmieniona. (Przesłania [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|  
|[CMFCToolBarDateTimeCtrl::OnMove](#onmove)|Wywoływane przez platformę, gdy przesuwa narzędzi nadrzędnej. (Przesłania [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|  
|[CMFCToolBarDateTimeCtrl::OnShow](#onshow)|Wywoływane przez platformę, gdy przycisk jest widoczny, czy niewidoczne. (Przesłania [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|  
|`CMFCToolBarDateTimeCtrl::OnSize`|Wywoływane przez platformę, gdy narzędzi nadrzędnego zmienia jego rozmiar lub położenie i ta zmiana powoduje, że przycisk, aby zmienić rozmiar. (Przesłania [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|  
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](#onupdatetooltip)|Wywoływane przez platformę, gdy jego tekst etykietki narzędzia aktualizacji narzędzi nadrzędnego. (Przesłania [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|  
|`CMFCToolBarDateTimeCtrl::Serialize`|Odczytuje obiekt z archiwum i zapisuje go do archiwum (zastępuje [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|  
|`CMFCToolBarDateTimeCtrl::SetStyle`|Ustawia styl przycisku paska narzędzi. (Przesłania [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|  
|[CMFCToolBarDateTimeCtrl::SetTime](#settime)|Ustawia datę i godzinę w formant wyboru godziny.|  
|[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)|Ustawia godzinę i datę we wszystkich wystąpieniach formant wyboru godziny, które mają identyfikator określonego polecenia.|  
  
## <a name="remarks"></a>Uwagi  
 Na przykład sposobu użycia formant wyboru daty i godziny Zobacz ToolbarDateTimePicker przykładowy projekt. Aby uzyskać informacje o sposobie dodawania przyciski sterowania paski narzędzi, zobacz [wskazówki: umieszczanie formantów na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxtoolbardatetimectrl.h  
  
##  <a name="canbestretched"></a>  CMFCToolBarDateTimeCtrl::CanBeStretched  
 Określa, czy użytkownik może stretch przycisku w trakcie dostosowywania realizowanego.  
  
```  
virtual BOOL CanBeStretched() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie platformę nie Zezwalaj użytkownikowi na stretch przycisku paska narzędzi w trakcie dostosowywania realizowanego. Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)), umożliwiając użytkownikowi stretch Data i godzina przycisku paska narzędzi w trakcie dostosowywania realizowanego.  
  
##  <a name="cmfctoolbardatetimectrl"></a>  CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl  
 Tworzy i inicjuje [CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md) obiektu.  
  
```  
CMFCToolBarDateTimeCtrl(
    UINT uiID,  
    int iImage,  
    DWORD dwStyle=0,  
    int iWidth=0);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *uiID*  
 Identyfikator formantu.  
  
 [in] *iImage*  
 Indeks obrazu na pasku narzędzi `CMFCToolBarImages` obiektu.  
  
 [in] *dwStyle*  
 Styl `CMFCToolBarDateTimeCtrlImpl` okna, który jest tworzony, gdy użytkownik kliknie przycisk.  
  
 [in] *iWidth*  
 Szerokość formantu w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Ten obiekt jest ustawiana na systemowej daty i godziny. Styl okna wewnętrznego `CMFCToolBarDateTimeCtrlImpl` obiekt zawiera *dwStyle* parametru i `WS_CHILD` i `WS_VISIBLE` style. Nie można zmienić tych stylów przy użyciu `CMFCToolBarDateTimeCtrl::SetStyle`. Użyj `SetStyle` do Zmień styl `CMFCToolBarDateTimeCtrl` formantu.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCToolBarDateTimeCtrl` klasy. Następujący fragment kodu jest częścią [próbki narzędzi wybór daty i godziny](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]  
  
##  <a name="copyfrom"></a>  CMFCToolBarDateTimeCtrl::CopyFrom  
 Kopiuje właściwości inny przycisk paska narzędzi do bieżącego przycisku.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *src*  
 Odwołanie do przycisku źródła do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody, aby skopiować inny przycisk paska narzędzi do tego przycisku paska narzędzi. *SRC* musi być typu `CMFCToolBarDateTimeCtrl`.  
  
##  <a name="exporttomenubutton"></a>  CMFCToolBarDateTimeCtrl::ExportToMenuButton  
 Kopiuje tekst przycisku paska narzędzi do menu.  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *przycisk menu*  
 Odwołanie do docelowego przycisku menu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje implementację klasy podstawowej ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) przez ładowanie zasobu ciągu skojarzonego z poleceniem o identyfikatorze formantu. Aby uzyskać więcej informacji na temat zasobów ciągu, zobacz [CStringT::LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring).  
  
##  <a name="getbycmd"></a>  CMFCToolBarDateTimeCtrl::GetByCmd  
 Pobiera pierwszy `CMFCToolBarDateTimeCtrl` obiektu w aplikacji, która ma identyfikator określonego polecenia.  
  
```  
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *uiCmd*  
 Identyfikator polecenia przycisku do pobrania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy `CMFCToolBarDateTimeCtrl` obiektów w aplikacji, która ma identyfikator określonego polecenia lub `NULL` Jeśli żadne `CMFCToolBarDateTimeCtrl` obiektów ma identyfikator określonego polecenia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jako narzędzia udostępnione jest używana przez metody, takie jak [CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall) i [CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall) ustawić lub pobrać godzinę i datę wszystkich wystąpień czasu formant wyboru, który ma identyfikator określonego polecenia.  
  
##  <a name="getdatetimectrl"></a>  CMFCToolBarDateTimeCtrl::GetDateTimeCtrl  
 Zwraca wskaźnik do formant wyboru daty i godziny.  
  
```  
CDateTimeCtrl* GetDateTimeCtrl() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do formant wyboru daty i godziny; lub `NULL` Jeśli formant nie istnieje.  
  
### <a name="remarks"></a>Uwagi  
 `CMFCToolBarDateTimeCtrl` Klasy inicjuje `m_pWndDateTime` element członkowski danych podczas wstawiania `CMFCToolBarDateTimeCtrl` obiektu na pasku narzędzi.  
  
##  <a name="gethwnd"></a>  CMFCToolBarDateTimeCtrl::GetHwnd  
 Pobiera uchwytu okna, który jest skojarzony z przycisku paska narzędzi.  
  
```  
virtual HWND GetHwnd();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Uchwyt okna, który jest skojarzony z przycisku paska narzędzi Data i godzina.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) metody.  
  
##  <a name="gettime"></a>  CMFCToolBarDateTimeCtrl::GetTime  
 Pobiera zaznaczony czas od daty skojarzone i formant wyboru godziny i umieszczenie go w określonym [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) — struktura  
  
```  
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out] *timeDest*  
 W pierwszym przeciążenia [klasy COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiekt, który otrzyma dotyczących czasu systemowego. W drugim przeciążenia [ctime —](../../atl-mfc-shared/reference/ctime-class.md) obiekt, który otrzyma dotyczących czasu systemowego.  
  
 [out] *pTimeDest*  
 Wskaźnik do [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktury otrzymywanie informacji czasu systemu. Nie może być `NULL`.  
  
### <a name="return-value"></a>Wartość zwracana  
 W pierwszym przeciążenia różną od zera, jeśli pomyślnie zapisane podczas [klasy COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiektu; w przeciwnym razie 0. W drugi i trzeci przeciążeń, jest zwracana wartość `DWORD` jest równa dwFlag elementu członkowskiego, który został ustawiony w [NMDATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761730) struktury.  
  
### <a name="remarks"></a>Uwagi  
 Ustawia metodę [NMDATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761730) struktury wartość elementu członkowskiego dwFlags wskazująca, czy selektora datę i godzinę ustawioną datę i godzinę. Jeśli wartość jest równa GDT_NONE, kontrolka jest ustawiony na `no date` stan i używa stylu DTS_SHOWNONE. Jeśli wartość zwracana równa GDT_VALID, czas systemowy pomyślnie znajduje się w lokalizacji docelowej.  
  
##  <a name="gettimeall"></a>  CMFCToolBarDateTimeCtrl::GetTimeAll  
 Zwraca godzinę wybrane przez użytkownika przycisku formantu selektora czas, który ma identyfikator określonego polecenia.  
  
```  
static BOOL GetTimeAll(
    UINT uiCmd,  
    COleDateTime& timeDest);

static DWORD GetTimeAll(
    UINT uiCmd,  
    CTime& timeDest);

static DWORD GetTimeAll(
    UINT uiCmd,  
    LPSYSTEMTIME pTimeDest);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *uiCmd*  
 Określa identyfikator przycisku paska narzędzi polecenia.  
  
 [out] *timeDest*  
 W pierwszym przeciążenia [klasy COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiekt, który otrzyma dotyczących czasu systemowego. W drugim przeciążenia [ctime —](../../atl-mfc-shared/reference/ctime-class.md) obiekt, który otrzyma dotyczących czasu systemowego.  
  
 [out] *pTimeDest*  
 Wskaźnik do [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktury otrzymywanie informacji czasu systemu. Nie może być `NULL`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli w ramach nie można odnaleźć przycisku paska narzędzi, który jest zgodny z Identyfikatorem polecenia *uiCmd*, jest zwracana wartość zero w pierwszym przeciążenia i GDT_NONE w inne przeciążenia. Jeśli zostanie znaleziony przycisku paska narzędzi, zwracana wartość jest taka sama jak wartość zwracana z wywołania [CMFCToolBarDateTimeCtrl::GetTime](#gettime) na tym przycisku. Zwracana wartość zero lub GDT_NONE może wystąpić, gdy przycisk zostanie znaleziony, który wskazuje, że wywołanie `GetTime` nie zwrócił prawidłową datą innego powodu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda sprawdza przycisku paska narzędzi z polecenie o określonym identyfikatorze i wywołania [CMFCToolBarDateTimeCtrl::GetTime](#gettime) metody dla tego przycisku.  
  
##  <a name="havehotborder"></a>  CMFCToolBarDateTimeCtrl::HaveHotBorder  
 Określa, czy obramowania przycisku jest wyświetlany, gdy użytkownik wybierze przycisk.  
  
```  
virtual BOOL HaveHotBorder() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli przycisku wyświetla jego obramowanie w przypadku wybrania; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wartość niezerową, jeśli formant jest widoczny.  
  
##  <a name="notifycommand"></a>  CMFCToolBarDateTimeCtrl::NotifyCommand  
 Określa, czy przycisk przetwarza [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) wiadomości.  
  
```  
virtual BOOL NotifyCommand(int iNotifyCode);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iNotifyCode*  
 Komunikat powiadomienia, który jest skojarzony z poleceniem.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli przycisk przetwarza komunikatów WM_COMMAND lub `FALSE` aby wskazać, że komunikat powinno zostać obsłużone przez nadrzędny paska narzędzi.  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tę metodę po zamiar wysłać [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) wiadomości do okna nadrzędnego.  
  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) przez przetwarzanie [dtn_datetimechange —](http://msdn.microsoft.com/library/windows/desktop/bb761737) powiadomień. Aktualizuje stan wewnętrzny czasu i aktualizuje właściwości czasu wszystkich `CMFCToolBarDateTimeCtrl` obiektów z takimi samymi polecenia identyfikatora.  
  
##  <a name="onaddtocustomizepage"></a>  CMFCToolBarDateTimeCtrl::OnAddToCustomizePage  
 Wywoływane przez platformę, gdy przycisk zostanie dodany do **Dostosuj** okno dialogowe.  
  
```  
virtual void OnAddToCustomizePage();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage), przez kopiowanie właściwości z pierwszą datę i godzinę sterowania wszystkie pasku narzędzi, która ma ten sam identyfikator polecenia co ten obiekt. Ta metoda nie działają, jeśli nie pasek narzędzi nie ma datę i godzinę formantu, który ma ten sam identyfikator polecenia co ten obiekt.  
  
 Aby uzyskać więcej informacji na temat **Dostosuj** okno dialogowe, zobacz [CMFCToolBarsCustomizeDialog klasy](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).  
  
##  <a name="onchangeparentwnd"></a>  CMFCToolBarDateTimeCtrl::OnChangeParentWnd  
 Wywoływane przez platformę, gdy przycisk jest wstawiany do nowego paska narzędzi.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pWndParent*  
 Nowe okno nadrzędne.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje implementację klasy podstawowej ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) tworząc wewnętrznej `CMFCToolBarDateTimeCtrlImpl` obiektu.  
  
##  <a name="onclick"></a>  CMFCToolBarDateTimeCtrl::OnClick  
 Wywoływane przez platformę, gdy użytkownik kliknie formantu.  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pWnd*  
 Nieużywane.  
  
 [in] *bDelay*  
 Nieużywane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli przycisku przetwarza wiadomości kliknij; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje implementację klasy podstawowej [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), zwracając wartość niezerową, jeśli wewnętrznej `CMFCToolBarDateTimeCtrlImpl` obiekt jest widoczny.  
  
##  <a name="onctlcolor"></a>  CMFCToolBarDateTimeCtrl::OnCtlColor  
 Wywoływane przez platformę, obsługując narzędzi nadrzędnej wm_ctlcolor — komunikat.  
  
```  
virtual HBRUSH OnCtlColor(
    CDC* pDC,  
    UINT nCtlColor);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
 Kontekst urządzenia wyświetlającego przycisku.  
  
 [in] *nCtlColor*  
 Nieużywane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do globalnego pędzel platformę używany do rysowania tła przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje implementację klasy podstawowej [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor), przez ustawienie tekstu i odpowiednio tła kolory kontekstu urządzenia udostępnionego do globalnego tekstu i kolory tła.  
  
 Aby uzyskać więcej informacji na temat opcji globalnych, które są dostępne dla aplikacji, zobacz [afx_global_data — struktura](../../mfc/reference/afx-global-data-structure.md).  
  
##  <a name="onglobalfontschanged"></a>  CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged  
 Wywoływane przez platformę, gdy globalne czcionka została zmieniona.  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)), zmieniając czcionki formantu w tym globalnych czcionki.  
  
 Aby uzyskać więcej informacji na temat opcji globalnych, które są dostępne dla aplikacji, zobacz [afx_global_data — struktura](../../mfc/reference/afx-global-data-structure.md).  
  
##  <a name="onmove"></a>  CMFCToolBarDateTimeCtrl::OnMove  
 Wywoływane przez platformę, gdy przesuwa narzędzi nadrzędnej.  
  
```  
virtual void OnMove();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje domyślną implementację klasy ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)), aktualizując pozycji wewnętrznego `CMFCToolBarDateTimeCtrlImpl` obiektu.  
  
##  <a name="onshow"></a>  CMFCToolBarDateTimeCtrl::OnShow  
 Wywoływane przez platformę, gdy przycisk jest widoczny, czy niewidoczne.  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bShow*  
 Określa, czy przycisk jest widoczny. Jeśli ten parametr ma `TRUE`, ten przycisk jest widoczny. W przeciwnym razie przycisk nie jest widoczny.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) za pomocą wyświetlania przycisku, jeśli *bShow* jest `TRUE`. W przeciwnym razie ta metoda powoduje ukrycie przycisku.  
  
##  <a name="onsize"></a>  CMFCToolBarDateTimeCtrl::OnSize  
 Wywoływane przez platformę, gdy narzędzi nadrzędnego zmienia jego rozmiar lub położenie i ta zmiana powoduje, że przycisk, aby zmienić rozmiar.  
  
```  
virtual void OnSize(int iSize);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iSize*  
 Nową szerokość przycisku w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje domyślną implementację klasy ( [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)), aktualizując rozmiar i położenie wewnętrznego `CMFCToolBarDateTimeCtrlImpl` obiektu.  
  
##  <a name="onupdatetooltip"></a>  CMFCToolBarDateTimeCtrl::OnUpdateToolTip  
 Wywoływane przez platformę, gdy jego tekst etykietki narzędzia aktualizacji narzędzi nadrzędnego.  
  
```  
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,  
    int iButtonIndex,  
    CToolTipCtrl& wndToolTip,  
    CString& str);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pWndParent*  
 Okno nadrzędne.  
  
 [in] *iButtonIndex*  
 Liczony od zera indeks w kolekcji nadrzędnej przycisk przycisk.  
  
 [in] *wndToolTip*  
 Formant, który wyświetla tekst elementu tooltip.  
  
 [out] *str*  
 A `CString` obiekt, który odbiera tekst etykietki narzędzia zaktualizowane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli metoda aktualizuje tekst etykietki narzędzia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) za pomocą wyświetlania tekst etykietki narzędzia, który jest skojarzony z przyciskiem. Jeśli przycisk nie jest zadokowany w poziomie, ta metoda nie działa i zwraca `FALSE`.  
  
##  <a name="settime"></a>  CMFCToolBarDateTimeCtrl::SetTime  
 Ustawia datę i godzinę w formant wyboru godziny.  
  
```  
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *timeNew*  
 W pierwszej wersji odwołania do [klasy COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiekt, który zawiera godzinę, do której zostanie ustawiona formantu. W drugiej wersji wskaźnik do [ctime —](../../atl-mfc-shared/reference/ctime-class.md) obiekt, który zawiera godzinę, do której zostanie ustawiona formantu.  
  
 [in] *pTimeNew*  
 Wskaźnik do [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) strukturę, która zawiera godzinę, do której zostanie ustawiona formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ustawia czas w formancie selektora daty i godziny, wywołując [CDateTimeCtrl::SetTime](../../mfc/reference/cdatetimectrl-class.md#settime).  
  
##  <a name="settimeall"></a>  CMFCToolBarDateTimeCtrl::SetTimeAll  
 Ustawia godzinę i datę we wszystkich wystąpieniach formant wyboru godziny, które mają identyfikator określonego polecenia.  
  
```  
static BOOL SetTimeAll(
    UINT uiCmd,  
    const COleDateTime& timeNew);

static BOOL SetTimeAll(
    UINT uiCmd,  
    const CTime* pTimeNew);

static BOOL SetTimeAll(
    UINT uiCmd,  
    LPSYSTEMTIME pTimeNew=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *uiCmd*  
 Określa identyfikator przycisku paska narzędzi polecenia.  
  
 [in] *timeNew*  
 W pierwszej wersji [klasy COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiekt, który zawiera godzinę, do której zostanie ustawiona formantu. W drugiej wersji wskaźnik do [ctime —](../../atl-mfc-shared/reference/ctime-class.md) obiekt, który zawiera godzinę, do której zostanie ustawiona formantu.  
  
 [in] *pTimeNew*  
 Wskaźnik do [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) strukturę, która zawiera godzinę, do której zostanie ustawiona formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wyszukuje przycisku paska narzędzi z polecenie o określonym identyfikatorze i ustawia czas w formancie selektora daty i godziny, wywołując [CMFCToolBarDateTimeCtrl::SetTime](#settime).  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Przewodnik: umieszczanie kontrolek na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)



