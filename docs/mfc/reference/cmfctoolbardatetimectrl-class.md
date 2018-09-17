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
ms.openlocfilehash: b2b1ee8e1beb6022d6a940e7036d9673e3844f35
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726729"
---
# <a name="cmfctoolbardatetimectrl-class"></a>Klasa CMFCToolBarDateTimeCtrl
Przycisk paska narzędzi, który zawiera kontrolkę selektora daty i godziny.  
  
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
|[CMFCToolBarDateTimeCtrl::CanBeStretched](#canbestretched)|Określa, czy użytkownik rozciągnąć przycisku podczas dostosowywania. (Przesłania [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|  
|[CMFCToolBarDateTimeCtrl::CopyFrom](#copyfrom)|Kopiuje bieżącego przycisku Właściwości inny przycisk paska narzędzi. (Przesłania [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|  
|`CMFCToolBarDateTimeCtrl::DuplicateData`|Zarezerwowane do użytku w przyszłości.|  
|[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|Kopiuje tekst na przycisku paska narzędzi do menu.|  
|`CMFCToolBarDateTimeCtrl::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|[CMFCToolBarDateTimeCtrl::GetByCmd](#getbycmd)|Pobiera pierwszy `CMFCToolBarDateTimeCtrl` obiektu w aplikacji, która ma identyfikator określonego polecenia.|  
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](#getdatetimectrl)|Zwraca wskaźnik do kontrolki selektora daty i godziny.|  
|[CMFCToolBarDateTimeCtrl::GetHwnd](#gethwnd)|Pobiera uchwyt okna, który jest skojarzony z przycisku paska narzędzi. (Przesłania [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|  
|`CMFCToolBarDateTimeCtrl::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|  
|[CMFCToolBarDateTimeCtrl::GetTime](#gettime)|Pobiera zaznaczony czas w kontrolce selektora daty i godziny i umieszcza go w określonej [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) struktury.|  
|[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)|Zwraca zaznaczony czas od przycisku kontrolki selektora czasu, który ma identyfikator określonego polecenia.|  
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](#havehotborder)|Określa, czy obramowanie przycisku jest wyświetlany, gdy użytkownik wybierze przycisk. (Przesłania [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|  
|[CMFCToolBarDateTimeCtrl::NotifyCommand](#notifycommand)|Określa, czy przycisk przetwarza [WM_COMMAND](/windows/desktop/menurc/wm-command) wiadomości. (Przesłania [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|  
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](#onaddtocustomizepage)|Wywoływane przez platformę, gdy przycisk zostanie dodany do **Dostosuj** okno dialogowe. (Przesłania [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|  
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|Metoda wywoływana przez platformę, by Oblicz rozmiar przycisku dla kontekstu określonego urządzenia i stan dokowania. (Przesłania [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|  
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](#onchangeparentwnd)|Wywoływane przez platformę, gdy przycisk znajduje się nowy pasek narzędzi. (Przesłania [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|  
|[CMFCToolBarDateTimeCtrl::OnClick](#onclick)|Wywoływane przez platformę, gdy użytkownik kliknie kontrolkę. (Przesłania [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|  
|[CMFCToolBarDateTimeCtrl::OnCtlColor](#onctlcolor)|Wywoływane przez platformę, obsługując narzędzi nadrzędnego wm_ctlcolor — komunikat. (Przesłania [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|  
|`CMFCToolBarDateTimeCtrl::OnDraw`|Metoda wywoływana przez platformę, by narysować przycisku przy użyciu określonych stylów i opcje. (Przesłania [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|  
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|Wywoływane przez platformę, by narysować przycisku **polecenia** okienku **Dostosuj** okno dialogowe. (Przesłania [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|  
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](#onglobalfontschanged)|Wywoływane przez platformę, gdy zmieniono globalnego czcionki. (Przesłania [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|  
|[CMFCToolBarDateTimeCtrl::OnMove](#onmove)|Wywoływane przez platformę, gdy przemieszczane narzędzi nadrzędnej. (Przesłania [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|  
|[CMFCToolBarDateTimeCtrl::OnShow](#onshow)|Wywoływane przez platformę, gdy przycisk staje się widoczny lub niewidoczny. (Przesłania [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|  
|`CMFCToolBarDateTimeCtrl::OnSize`|Wywoływane przez platformę, gdy narzędzi nadrzędnego zmienia jego rozmiar lub położenie i ta zmiana powoduje, że przycisk, aby zmienić rozmiar. (Przesłania [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|  
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](#onupdatetooltip)|Wywoływane przez platformę, gdy narzędzi nadrzędnego aktualizuje jego tekst etykietki narzędzia. (Przesłania [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|  
|`CMFCToolBarDateTimeCtrl::Serialize`|Odczytuje obiekt z archiwum lub zapisuje je do archiwum (zastępuje [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|  
|`CMFCToolBarDateTimeCtrl::SetStyle`|Ustawia styl przycisku paska narzędzi. (Przesłania [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|  
|[CMFCToolBarDateTimeCtrl::SetTime](#settime)|Ustawia datę i godzinę w kontrolce selektora czasu.|  
|[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)|Ustawia datę i godzinę we wszystkich wystąpieniach formant selektora czasu, które mają identyfikator określonego polecenia.|  
  
## <a name="remarks"></a>Uwagi  
 Na przykład jak używać kontrolkę selektora daty i godziny Zobacz ToolbarDateTimePicker przykładowy projekt. Aby uzyskać informacje dotyczące sposobu dodawania przycisków kontrolnych paski narzędzi, zobacz [wskazówki: umieszczanie formantów na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxtoolbardatetimectrl.h  
  
##  <a name="canbestretched"></a>  CMFCToolBarDateTimeCtrl::CanBeStretched  
 Określa, czy użytkownik rozciągnąć przycisku podczas dostosowywania.  
  
```  
virtual BOOL CanBeStretched() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca wartość TRUE.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie struktura nie zezwala użytkownikowi stretch przycisku paska narzędzi podczas dostosowywania. Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)), umożliwiając użytkownikowi stretch przycisku paska narzędzi daty i godziny podczas dostosowywania.  
  
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
*uiID*<br/>
[in] Identyfikator kontrolki.  
  
*iImage*<br/>
[in] Indeks obrazu, na pasku narzędzi `CMFCToolBarImages` obiektu.  
  
*dwStyle*<br/>
[in] Styl `CMFCToolBarDateTimeCtrlImpl` okna, który jest tworzony, gdy użytkownik kliknie przycisk.  
  
*iWidth*<br/>
[in] Szerokość formantu w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Ten obiekt jest inicjowany do systemowej daty i godziny. Styl okna wewnętrznego `CMFCToolBarDateTimeCtrlImpl` obiekt zawiera *dwStyle* parametr i style WS_CHILD i WS_VISIBLE. Nie można zmienić te style, przy użyciu `CMFCToolBarDateTimeCtrl::SetStyle`. Użyj `SetStyle` zmienić styl `CMFCToolBarDateTimeCtrl` kontroli.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCToolBarDateTimeCtrl` klasy. Ten fragment kodu jest częścią [przykładowy wybór daty i godziny narzędzi](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]  
  
##  <a name="copyfrom"></a>  CMFCToolBarDateTimeCtrl::CopyFrom  
 Kopiuje bieżącego przycisku Właściwości inny przycisk paska narzędzi.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parametry  
*src*<br/>
[in] Odwołanie do przycisku źródła do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby skopiować inny przycisk paska narzędzi do tego przycisku paska narzędzi. *SRC* musi być typu `CMFCToolBarDateTimeCtrl`.  
  
##  <a name="exporttomenubutton"></a>  CMFCToolBarDateTimeCtrl::ExportToMenuButton  
 Kopiuje tekst na przycisku paska narzędzi do menu.  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>Parametry  
*Przycisk menu*<br/>
[in] Odwołanie do docelowego przycisku menu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca wartość TRUE.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje implementacji klasy podstawowej ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)), ładując zasobu ciągu, który jest skojarzony z poleceniem o identyfikatorze formantu. Aby uzyskać więcej informacji na temat zasobów ciągów zobacz [CStringT::LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring).  
  
##  <a name="getbycmd"></a>  CMFCToolBarDateTimeCtrl::GetByCmd  
 Pobiera pierwszy `CMFCToolBarDateTimeCtrl` obiektu w aplikacji, która ma identyfikator określonego polecenia.  
  
```  
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
*uiCmd*<br/>
[in] Identyfikator polecenia przycisku do pobrania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy `CMFCToolBarDateTimeCtrl` obiektu w aplikacji, który zawiera polecenie o określonym identyfikatorze lub o wartości NULL, jeśli nie `CMFCToolBarDateTimeCtrl` obiektów ma identyfikator określonego polecenia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda narzędzia udostępnione jest używana przez metody takie jak [CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall) i [CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall) można ustawiać ani pobierać Data i godzina wszystkich wystąpień czasu Kontrolka selektora, który ma identyfikator określonego polecenia.  
  
##  <a name="getdatetimectrl"></a>  CMFCToolBarDateTimeCtrl::GetDateTimeCtrl  
 Zwraca wskaźnik do kontrolki selektora daty i godziny.  
  
```  
CDateTimeCtrl* GetDateTimeCtrl() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do kontrolki selektora daty i godziny; lub wartość NULL, jeśli formant nie istnieje.  
  
### <a name="remarks"></a>Uwagi  
 `CMFCToolBarDateTimeCtrl` Klasy inicjuje `m_pWndDateTime` element członkowski danych podczas wstawiania `CMFCToolBarDateTimeCtrl` obiektu do paska narzędzi.  
  
##  <a name="gethwnd"></a>  CMFCToolBarDateTimeCtrl::GetHwnd  
 Pobiera uchwyt okna, który jest skojarzony z przycisku paska narzędzi.  
  
```  
virtual HWND GetHwnd();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Uchwyt okna, który jest skojarzony z przycisku paska narzędzi daty i godziny.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) metody.  
  
##  <a name="gettime"></a>  CMFCToolBarDateTimeCtrl::GetTime  
 Pobiera zaznaczony czas z skojarzone daty i czasu kontrolkę selektora i umieszcza go w określonej [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) struktury  
  
```  
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;  
```  
  
### <a name="parameters"></a>Parametry  
*timeDest*<br/>
[out] W pierwsze przeciążenie [COleDateTime, klasa](../../atl-mfc-shared/reference/coledatetime-class.md) obiektu, który będzie otrzymywać informacji dotyczących czasu systemowego. W drugie przeciążenie [CTime](../../atl-mfc-shared/reference/ctime-class.md) obiektu, który będzie otrzymywać informacji dotyczących czasu systemowego.  
  
*pTimeDest*<br/>
[out] Wskaźnik do [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) strukturę do odbierania informacji o czasie systemu. Nie może mieć wartości NULL.  
  
### <a name="return-value"></a>Wartość zwracana  
 W pierwsze przeciążenie wartość różną od zera, jeśli pomyślnie zapisane czas [COleDateTime, klasa](../../atl-mfc-shared/reference/coledatetime-class.md) obiektu; w przeciwnym razie 0. W drugi i trzeci przeciążeń, wartość zwracana jest typu DWORD, który jest równy dwFlag elementu członkowskiego, która została ustawiona w [NMDATETIMECHANGE](/windows/desktop/api/commctrl/ns-commctrl-tagnmdatetimechange) struktury.  
  
### <a name="remarks"></a>Uwagi  
 Metody ustawia [NMDATETIMECHANGE](/windows/desktop/api/commctrl/ns-commctrl-tagnmdatetimechange) struktury Flagidw elementu członkowskiego, aby wskazać, czy selektor daty i godziny jest ustawiona na datę i godzinę. Jeśli wartość jest równa GDT_NONE, kontrolki jest ustawiony na `no date` stan i używa stylu DTS_SHOWNONE. Jeśli wartość zwracana równa GDT_VALID, czas systemowy zostały pomyślnie zapisane w lokalizacji docelowej.  
  
##  <a name="gettimeall"></a>  CMFCToolBarDateTimeCtrl::GetTimeAll  
 Zwraca czas wybrane przez użytkownika przy użyciu przycisku kontroli selektor czasu, który ma identyfikator określonego polecenia.  
  
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
*uiCmd*<br/>
[in] Określa identyfikator przycisku paska narzędzi polecenia.  
  
*timeDest*<br/>
[out] W pierwsze przeciążenie [COleDateTime, klasa](../../atl-mfc-shared/reference/coledatetime-class.md) obiektu, który będzie otrzymywać informacji dotyczących czasu systemowego. W drugie przeciążenie [CTime](../../atl-mfc-shared/reference/ctime-class.md) obiektu, który będzie otrzymywać informacji dotyczących czasu systemowego.  
  
*pTimeDest*<br/>
[out] Wskaźnik do [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) strukturę do odbierania informacji o czasie systemu. Nie może mieć wartości NULL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli w ramach nie można odnaleźć przycisku paska narzędzi, który jest zgodny z Identyfikatorem polecenia *uiCmd*, wartość zwracana to zero w pierwsze przeciążenie i GDT_NONE w inne przeciążenia. Jeśli zostanie znaleziony przycisku paska narzędzi, zwracana wartość jest taka sama jak wartość zwracaną z wywołania do [CMFCToolBarDateTimeCtrl::GetTime](#gettime) tego przycisku. Zwracana wartość zero lub GDT_NONE może wystąpić, gdy zostanie znaleziony przycisku, który wskazuje, że wywołanie `GetTime` nie zwrócił prawidłową datę innego powodu.  
  
### <a name="remarks"></a>Uwagi  
 Metoda ta wyszukuje przycisk paska narzędzi, który posiada polecenie o określonym identyfikatorze i wywołania [CMFCToolBarDateTimeCtrl::GetTime](#gettime) metody tego przycisku.  
  
##  <a name="havehotborder"></a>  CMFCToolBarDateTimeCtrl::HaveHotBorder  
 Określa, czy obramowanie przycisku jest wyświetlany, gdy użytkownik wybierze przycisk.  
  
```  
virtual BOOL HaveHotBorder() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli przycisk powoduje wyświetlenie jego obramowanie po wybraniu; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wartość różną od zera, jeśli kontrolka jest widoczna.  
  
##  <a name="notifycommand"></a>  CMFCToolBarDateTimeCtrl::NotifyCommand  
 Określa, czy przycisk przetwarza [WM_COMMAND](/windows/desktop/menurc/wm-command) wiadomości.  
  
```  
virtual BOOL NotifyCommand(int iNotifyCode);
```  
  
### <a name="parameters"></a>Parametry  
*iNotifyCode*<br/>
[in] Komunikat powiadomienia, który jest skojarzony z poleceniem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przycisk przetwarza komunikatów WM_COMMAND, lub FAŁSZ, aby wskazać, że komunikat powinno zostać obsłużone przez narzędzi nadrzędnego.  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tę metodę po około do wysyłania [WM_COMMAND](/windows/desktop/menurc/wm-command) wiadomości do okna nadrzędnego.  
  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) przez przetwarzanie [dtn_datetimechange —](/windows/desktop/Controls/dtn-datetimechange) powiadomień. Aktualizuje stan wewnętrzny czasu i aktualizuje właściwości godziny wszystkie `CMFCToolBarDateTimeCtrl` obiekty o takiej samej polecenia identyfikatora.  
  
##  <a name="onaddtocustomizepage"></a>  CMFCToolBarDateTimeCtrl::OnAddToCustomizePage  
 Wywoływane przez platformę, gdy przycisk zostanie dodany do **Dostosuj** okno dialogowe.  
  
```  
virtual void OnAddToCustomizePage();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage), przez kopiowanie właściwości z pierwszą datę i godzinę kontrolki w dowolnym pasek narzędzi, który ma ten sam identyfikator polecenia, jak ten obiekt. Ta metoda nie działają, jeśli brak paska narzędzi zawiera datę i godzinę formant, który ma ten sam identyfikator polecenia, jak ten obiekt.  
  
 Aby uzyskać więcej informacji na temat **Dostosuj** okno dialogowe, zobacz [klasa CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).  
  
##  <a name="onchangeparentwnd"></a>  CMFCToolBarDateTimeCtrl::OnChangeParentWnd  
 Wywoływane przez platformę, gdy przycisk znajduje się nowy pasek narzędzi.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parametry  
*pWndParent*<br/>
[in] Nowe okno nadrzędne.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje implementacji klasy podstawowej ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)), ponownie tworząc wewnętrzny `CMFCToolBarDateTimeCtrlImpl` obiektu.  
  
##  <a name="onclick"></a>  CMFCToolBarDateTimeCtrl::OnClick  
 Wywoływane przez platformę, gdy użytkownik kliknie kontrolkę.  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
*pWnd*<br/>
[in] Nieużywane.  
  
*bDelay*<br/>
[in] Nieużywane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli przycisk przetwarza wiadomości kliknij; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje implementacji klasy podstawowej [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), zwracając wartość różną od zera, jeśli wewnętrzny `CMFCToolBarDateTimeCtrlImpl` obiekt jest widoczny.  
  
##  <a name="onctlcolor"></a>  CMFCToolBarDateTimeCtrl::OnCtlColor  
 Wywoływane przez platformę, obsługując narzędzi nadrzędnego wm_ctlcolor — komunikat.  
  
```  
virtual HBRUSH OnCtlColor(
    CDC* pDC,  
    UINT nCtlColor);
```  
  
### <a name="parameters"></a>Parametry  
*podstawowego kontrolera domeny*<br/>
[in] Kontekst urządzenia, które powoduje wyświetlenie przycisku.  
  
*nCtlColor*<br/>
[in] Nieużywane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do globalnego pędzel środowisko wykorzystuje do malowania tło przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje implementacji klasy podstawowej [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)przez ustawienie tekstu i tła kolorów kontekstu urządzenia podanego w tekście globalnych i kolory tła, odpowiednio.  
  
 Aby uzyskać więcej informacji na temat opcji globalnych, które są dostępne dla aplikacji, zobacz [afx_global_data — struktura](../../mfc/reference/afx-global-data-structure.md).  
  
##  <a name="onglobalfontschanged"></a>  CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged  
 Wywoływane przez platformę, gdy zmieniono globalnego czcionki.  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)), zmieniając czcionki formantu z globalnego czcionki.  
  
 Aby uzyskać więcej informacji na temat opcji globalnych, które są dostępne dla aplikacji, zobacz [afx_global_data — struktura](../../mfc/reference/afx-global-data-structure.md).  
  
##  <a name="onmove"></a>  CMFCToolBarDateTimeCtrl::OnMove  
 Wywoływane przez platformę, gdy przemieszczane narzędzi nadrzędnej.  
  
```  
virtual void OnMove();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje domyślna Implementacja klasy ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)), aktualizując pozycji wewnętrznego `CMFCToolBarDateTimeCtrlImpl` obiektu.  
  
##  <a name="onshow"></a>  CMFCToolBarDateTimeCtrl::OnShow  
 Wywoływane przez platformę, gdy przycisk staje się widoczny lub niewidoczny.  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
*bShow*<br/>
[in] Określa, czy przycisk jest widoczny. Jeśli ten parametr ma wartość TRUE, ten przycisk jest widoczna. W przeciwnym razie przycisk nie jest widoczna.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) za pomocą wyświetlania przycisku, jeśli *bShow* ma wartość TRUE. W przeciwnym razie ta metoda powoduje ukrycie przycisku.  
  
##  <a name="onsize"></a>  CMFCToolBarDateTimeCtrl::OnSize  
 Wywoływane przez platformę, gdy narzędzi nadrzędnego zmienia jego rozmiar lub położenie i ta zmiana powoduje, że przycisk, aby zmienić rozmiar.  
  
```  
virtual void OnSize(int iSize);
```  
  
### <a name="parameters"></a>Parametry  
*iSize*<br/>
[in] Szerokość nowy przycisk, w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje domyślna Implementacja klasy ( [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)), aktualizując rozmiar i położenie wewnętrznego `CMFCToolBarDateTimeCtrlImpl` obiektu.  
  
##  <a name="onupdatetooltip"></a>  CMFCToolBarDateTimeCtrl::OnUpdateToolTip  
 Wywoływane przez platformę, gdy narzędzi nadrzędnego aktualizuje jego tekst etykietki narzędzia.  
  
```  
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,  
    int iButtonIndex,  
    CToolTipCtrl& wndToolTip,  
    CString& str);
```  
  
### <a name="parameters"></a>Parametry  
*pWndParent*<br/>
[in] Okno nadrzędne.  
  
*iButtonIndex*<br/>
[in] Liczony od zera indeks przycisku w kolekcji przycisk nadrzędnej.  
  
*wndToolTip*<br/>
[in] Formant, który wyświetla tekst etykietki narzędzia.  
  
*str*<br/>
[out] A `CString` obiekt, który odbiera tekst etykietki narzędzia zaktualizowane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli metoda aktualizuje tekst etykietki narzędzia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)), wyświetlając tekst etykietki narzędzia, który jest skojarzony z przyciskiem. Jeśli przycisk nie jest zadokowany w poziomie, ta metoda nic nie robi i zwraca wartość FALSE.  
  
##  <a name="settime"></a>  CMFCToolBarDateTimeCtrl::SetTime  
 Ustawia datę i godzinę w kontrolce selektora czasu.  
  
```  
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```  
  
### <a name="parameters"></a>Parametry  
*timeNew*<br/>
[in] W pierwszej wersji odwołania do [COleDateTime, klasa](../../atl-mfc-shared/reference/coledatetime-class.md) obiekt, który zawiera godzinę, do której formant zostanie ustawiony. W drugiej wersji, wskaźnik do [CTime](../../atl-mfc-shared/reference/ctime-class.md) obiekt, który zawiera godzinę, do której formant zostanie ustawiony.  
  
*pTimeNew*<br/>
[in] Wskaźnik do [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) strukturę, która zawiera godzinę, do której formant zostanie ustawiony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Określa czas w kontrolce selektora daty i godziny, wywołując [CDateTimeCtrl::SetTime](../../mfc/reference/cdatetimectrl-class.md#settime).  
  
##  <a name="settimeall"></a>  CMFCToolBarDateTimeCtrl::SetTimeAll  
 Ustawia datę i godzinę we wszystkich wystąpieniach formant selektora czasu, które mają identyfikator określonego polecenia.  
  
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
*uiCmd*<br/>
[in] Określa identyfikator przycisku paska narzędzi polecenia.  
  
*timeNew*<br/>
[in] W pierwszej wersji [COleDateTime, klasa](../../atl-mfc-shared/reference/coledatetime-class.md) obiekt, który zawiera godzinę, do której formant zostanie ustawiony. W drugiej wersji, wskaźnik do [CTime](../../atl-mfc-shared/reference/ctime-class.md) obiekt, który zawiera godzinę, do której formant zostanie ustawiony.  
  
*pTimeNew*<br/>
[in] Wskaźnik do [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) strukturę, która zawiera godzinę, do której formant zostanie ustawiony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wyszukuje dla przycisku kontrolki toolbar przy użyciu polecenie o określonym identyfikatorze i ustawia czas w kontrolce selektora daty i godziny, wywołując [CMFCToolBarDateTimeCtrl::SetTime](#settime).  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Przewodnik: umieszczanie kontrolek na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)



