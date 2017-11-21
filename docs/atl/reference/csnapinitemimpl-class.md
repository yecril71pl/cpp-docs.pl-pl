---
title: Klasa CSnapInItemImpl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl::CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl::AddMenuItems
- ATLSNAP/ATL::CSnapInItemImpl::Command
- ATLSNAP/ATL::CSnapInItemImpl::CreatePropertyPages
- ATLSNAP/ATL::CSnapInItemImpl::FillData
- ATLSNAP/ATL::CSnapInItemImpl::GetResultPaneInfo
- ATLSNAP/ATL::CSnapInItemImpl::GetResultViewType
- ATLSNAP/ATL::CSnapInItemImpl::GetScopePaneInfo
- ATLSNAP/ATL::CSnapInItemImpl::Notify
- ATLSNAP/ATL::CSnapInItemImpl::QueryPagesFor
- ATLSNAP/ATL::CSnapInItemImpl::SetMenuInsertionFlags
- ATLSNAP/ATL::CSnapInItemImpl::SetToolbarButtonInfo
- ATLSNAP/ATL::CSnapInItemImpl::UpdateMenuState
- ATLSNAP/ATL::CSnapInItemImpl::UpdateToolbarButton
- ATLSNAP/ATL::CSnapInItemImpl::m_bstrDisplayName
- ATLSNAP/ATL::CSnapInItemImpl::m_resultDataItem
- ATLSNAP/ATL::CSnapInItemImpl::m_scopeDataItem
dev_langs: C++
helpviewer_keywords:
- snap-ins, data items
- snap-ins, ATL support for
- CSnapInItemImpl class
- snap-ins
ms.assetid: 52caefbd-9eae-49b0-add2-d55524271aa7
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1758a3d3bec03015abf35626adec69e1db9a7fdb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="csnapinitemimpl-class"></a>Klasa CSnapInItemImpl
Ta klasa dostarcza metody implementacji obiektu węzła przystawki.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T, BOOL bIsExtension = FALSE>  
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `CSnapInItemImpl`.  
  
 *bIsExtension*  
 **Wartość TRUE,** Jeśli obiekt jest rozszerzeniem przystawki; w przeciwnym razie **FALSE**.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSnapInItemImpl::CSnapInItemImpl](#csnapinitemimpl)|Konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSnapInItemImpl::AddMenuItems](#addmenuitems)|Dodaje elementy menu do menu kontekstowego.|  
|[CSnapInItemImpl::Command](#command)|Metoda wywoływana przez konsolę, po wybraniu elementu menu niestandardowe.|  
|[CSnapInItemImpl::CreatePropertyPages](#createpropertypages)|Dodaje strony do arkusza właściwości przystawki.|  
|[CSnapInItemImpl::FillData](#filldata)|Informacje kopii obiektu przystawki do określonego strumienia.|  
|[CSnapInItemImpl::GetResultPaneInfo](#getresultpaneinfo)|Pobiera **RESULTDATAITEM** struktury przystawki.|  
|[CSnapInItemImpl::GetResultViewType](#getresultviewtype)|Określa typ widoku, w okienku wyników.|  
|[CSnapInItemImpl::GetScopePaneInfo](#getscopepaneinfo)|Pobiera **SCOPEDATAITEM** struktury przystawki.|  
|[CSnapInItemImpl::Notify](#notify)|Metoda wywoływana przez konsolę, aby powiadomić przystawki o działaniach podjętych przez użytkownika.|  
|[CSnapInItemImpl::QueryPagesFor](#querypagesfor)|Wywołuje się, czy węzeł przystawki obsługuje strony właściwości.|  
|[CSnapInItemImpl::SetMenuInsertionFlags](#setmenuinsertionflags)|Modyfikuje flagi wstawiania menu dla obiekt przystawki.|  
|[CSnapInItemImpl::SetToolbarButtonInfo](#settoolbarbuttoninfo)|Ustawia informacje o przycisku paska narzędzi określony.|  
|[CSnapInItemImpl::UpdateMenuState](#updatemenustate)|Aktualizuje stan elementu menu kontekstowego.|  
|[CSnapInItemImpl::UpdateToolbarButton](#updatetoolbarbutton)|Aktualizuje stan przycisku paska narzędzi określony.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSnapInItemImpl::m_bstrDisplayName](#m_bstrdisplayname)|Nazwa obiektu przystawki.|  
|[CSnapInItemImpl::m_resultDataItem](#m_resultdataitem)|Windows **RESULTDATAITEM** struktury używane przez `CSnapInItemImpl` obiektu.|  
|[CSnapInItemImpl::m_scopeDataItem](#m_scopedataitem)|Windows **SCOPEDATAITEM** struktury używane przez `CSnapInItemImpl` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `CSnapInItemImpl`udostępnia podstawową implementację obiektu przystawki węzeł, na przykład dodawanie elementów menu i pasków narzędzi oraz przekazywania poleceń dla funkcji obsługi odpowiedniego węzła przystawki. Te funkcje są implementowane za pomocą kilku różnych interfejsach i mapowania typów. Domyślna implementacja obsługuje powiadomień wysyłanych do obiektu węzła przez określenie poprawne wystąpienie klasy pochodnej, a następnie przekazywania wiadomości na prawidłowe wystąpienie.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CSnapInItem`  
  
 `CSnapInItemImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsnap.h  
  
##  <a name="addmenuitems"></a>CSnapInItemImpl::AddMenuItems  
 Ta metoda implementuje funkcję Win32 [IExtendContextMenu::AddMenuItems](http://msdn.microsoft.com/library/aa814841).  
  
```
AddMenuItems(  
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```  
  
### <a name="parameters"></a>Parametry  
 *piCallback*  
 [in] Wskaźnik do **IContextMenuCallback** które można dodać elementy do menu kontekstowego.  
  
 `pInsertionAllowed`  
 [w, out] Identyfikuje zdefiniowane konsoli programu MMC, element menu wstawiania punkty, które mogą być używane. Może to być kombinacją następujące flagi:  
  
- **CCM_INSERTIONALLOWED_TOP** elementy mogą być wstawiane w górnej części menu kontekstowego.  
  
- **CCM_INSERTIONALLOWED_NEW** można wstawiać elementy podmenu Utwórz nowy.  
  
- **CCM_INSERTIONALLOWED_TASK** można wstawiać elementy w menu zadania.  
  
- **CCM_INSERTIONALLOWED_VIEW** można wstawiać elementy w menu Widok paska narzędzi lub w podmenu Widok z menu kontekstowe okienka wyników.  
  
 `type`  
 [in] Określa typ obiektu. Może mieć jedną z następujących wartości:  
  
- **CCT_SCOPE** obiektu dla kontekstu zakresu okienka.  
  
- **CCT_RESULT** obiektu dla kontekstu w okienku wyników.  
  
- **CCT_SNAPIN_MANAGER** obiektu dla kontekstu przystawki Menedżer.  
  
- **CCT_UNINITIALIZED** obiekt danych ma nieprawidłowy typ.  
  
##  <a name="command"></a>CSnapInItemImpl::Command  
 Ta metoda implementuje funkcję Win32 [IExtendContextMenu::Command](http://msdn.microsoft.com/library/aa814842).  
  
```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```  
  
### <a name="parameters"></a>Parametry  
 *lCommandID*  
 [in] Określa identyfikator polecenia elementu menu.  
  
 `type`  
 [in] Określa typ obiektu. Może mieć jedną z następujących wartości:  
  
- **CCT_SCOPE** obiektu dla kontekstu zakresu okienka.  
  
- **CCT_RESULT** obiektu dla kontekstu w okienku wyników.  
  
- **CCT_SNAPIN_MANAGER** obiektu dla kontekstu przystawki Menedżer.  
  
- **CCT_UNINITIALIZED** obiekt danych ma nieprawidłowy typ.  
  
##  <a name="createpropertypages"></a>CSnapInItemImpl::CreatePropertyPages  
 Ta metoda implementuje funkcję Win32 [IExtendPropertySheet::CreatePropertyPages](http://msdn.microsoft.com/library/aa814846).  
  
```
CreatePropertyPages(  
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```  
  
### <a name="parameters"></a>Parametry  
 *lpProvider*  
 [in] Wskaźnik do **IPropertySheetCallback** interfejsu.  
  
 *dojście*  
 [in] Określa uchwyt używany do trasy **MMCN_PROPERTY_CHANGE** wiadomość z powiadomieniem do klasy odpowiednie dane.  
  
 *pUnk*  
 [in] Wskaźnik do **IExtendPropertySheet** interfejsu dla obiektu, który zawiera informacje o kontekście dotyczące węzła.  
  
 `type`  
 [in] Określa typ obiektu. Może mieć jedną z następujących wartości:  
  
- **CCT_SCOPE** obiektu dla kontekstu zakresu okienka.  
  
- **CCT_RESULT** obiektu dla kontekstu w okienku wyników.  
  
- **CCT_SNAPIN_MANAGER** obiektu dla kontekstu przystawki Menedżer.  
  
- **CCT_UNINITIALIZED** obiekt danych ma nieprawidłowy typ.  
  
##  <a name="csnapinitemimpl"></a>CSnapInItemImpl::CSnapInItemImpl  
 Konstruuje `CSnapInItemImpl` obiektu.  
  
```
CSnapInItemImpl();
```  
  
##  <a name="filldata"></a>CSnapInItemImpl::FillData  
 Ta funkcja jest wywoływana w celu uzyskania informacji o elemencie.  
  
```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```  
  
### <a name="parameters"></a>Parametry  
 `cf`  
 [in] Format (tekst tekstu sformatowanego i tekstu sformatowanego z elementami OLE) Schowka.  
  
 `pStream`  
 [in] Wskaźnik do strumienia zawierający dane obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Aby prawidłowo zaimplementować tę funkcję, należy skopiować poprawnych informacji do strumienia ( `pStream`), w zależności od formatu Schowka wskazywanym przez `cf`.  
  
##  <a name="getresultviewtype"></a>CSnapInItemImpl::GetResultViewType  
 Wywołanie tej funkcji można pobrać typu widoku dla okienka wyników przystawki obiektu.  
  
```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```  
  
### <a name="parameters"></a>Parametry  
 *ppViewType*  
 [out] Wskaźnik do adresu typu widoku zwrócony.  
  
 *pViewOptions*  
 [out] Wskaźnik do **MMC_VIEW_OPTIONS** wyliczenia, co zapewnia konsoli z opcjami przystawkę będący właścicielem. Ta wartość może być jedną z następujących czynności:  
  
- **MMC_VIEW_OPTIONS_NOLISTVIEWS** = 0x00000001 informuje konsoli zaniechania przedstawiający standardowe listami wyboru widoku w **widoku** menu. Umożliwia przystawki do wyświetlenia tylko w okienku wyników widoku własnych widoków niestandardowych. Jest to tylko flaga opcji zdefiniowane w tym momencie.  
  
- **MMC_VIEW_OPTIONS_NONE** = 0 umożliwia domyślne opcje widoku.  
  
##  <a name="getscopepaneinfo"></a>CSnapInItemImpl::GetScopePaneInfo  
 Wywołanie tej funkcji można pobrać **SCOPEDATAITEM** struktury przystawki.  
  
```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```  
  
### <a name="parameters"></a>Parametry  
 *pScopeDataItem*  
 [out] Wskaźnik do **SCOPEDATAITEM** struktury `CSnapInItemImpl` obiektu.  
  
##  <a name="getresultpaneinfo"></a>CSnapInItemImpl::GetResultPaneInfo  
 Wywołanie tej funkcji można pobrać **RESULTDATAITEM** struktury przystawki.  
  
```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```  
  
### <a name="parameters"></a>Parametry  
 *pResultDataItem*  
 [out] Wskaźnik do **RESULTDATAITEM** struktury `CSnapInItemImpl` obiektu.  
  
##  <a name="m_bstrdisplayname"></a>CSnapInItemImpl::m_bstrDisplayName  
 Zawiera ciąg wyświetlany dla elementu węzła.  
  
```
CComBSTR m_bstrDisplayName;
```  
  
##  <a name="m_scopedataitem"></a>CSnapInItemImpl::m_scopeDataItem  
 `SCOPEDATAITEM` Strukturę obiektu danych przystawki.  
  
```
SCOPEDATAITEM m_scopeDataItem;
```  
  
##  <a name="m_resultdataitem"></a>CSnapInItemImpl::m_resultDataItem  
 [RESULTDATAITEM](http://msdn.microsoft.com/library/aa815165) strukturę obiektu danych przystawki.  
  
```
RESULTDATAITEM m_resultDataItem;
```  
  
##  <a name="notify"></a>CSnapInItemImpl::Notify  
 Wywoływane, gdy obiekt przystawki jest reagować przez użytkownika.  
  
```
STDMETHOD(Notify)(
    MMC_NOTIFY_TYPE event,
    long arg,
    long param,
    IComponentData* pComponentData,
    IComponent* pComponent,
    DATA_OBJECT_TYPES type) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `event`  
 [in] Określa akcję wykonywaną przez użytkownika. Możliwe są następujące powiadomienia:  
  
- **MMCN_ACTIVATE** wysyłany, gdy okno jest aktywowana i dezaktywowane.  
  
- **MMCN_ADD_IMAGES** wysyłane do dodawania obrazów w okienku wyników.  
  
- **MMCN_BTN_CLICK** wysyłany, gdy użytkownik kliknie jeden z przycisków paska narzędzi.  
  
- **MMCN_CLICK** wysyłany, gdy użytkownik kliknie przycisk myszy elementu widoku listy.  
  
- **MMCN_DBLCLICK** wysyłany, gdy dwukrotnie kliknięty przycisk myszy elementu widoku listy.  
  
- **MMCN_DELETE** wysyłane do informowania przystawki, który powinien być obiekt usunięte.  
  
- **MMCN_EXPAND** wysyłany, gdy folder musi być rozwinięty lub zaistniałych.  
  
- **MMCN_MINIMIZED** wysyłany, gdy okno jest zminimalizowane lub zmaksymalizowane.  
  
- **MMCN_PROPERTY_CHANGE** wysyłane w celu powiadomienia obiektu przystawki, który ma zmienić widok przystawki obiektu.  
  
- **MMCN_REMOVE_CHILDREN** wysyłany, gdy przystawkę, należy usunąć całe poddrzewo został dodany poniżej określonego węzła.  
  
- **MMCN_RENAME** wysyłane po raz pierwszy w zapytaniu do zmiany nazwy i po raz drugi do zmiany nazwy.  
  
- **MMCN_SELECT** wysyłane po wybraniu elementu w zakresie lub wynik w okienku widoku.  
  
- **MMCN_SHOW** wysyłany, gdy element zakresu jest zaznaczany lub odznaczany po raz pierwszy.  
  
- **MMCN_VIEW_CHANGE** wysyłany, gdy ta przystawka aktualizowania wszystkich widoków, gdy nastąpi zmiana.  
  
 `arg`  
 [in] Zależy od typu powiadomienia.  
  
 `param`  
 [in] Zależy od typu powiadomienia.  
  
 *pComponentData*  
 [out] Wskaźnik do obiektu implementujący **IComponentData**. Ten parametr jest **NULL** Jeśli powiadomienia nie są przekazywane z **IComponentData::Notify**.  
  
 *pComponent*  
 [out] Wskaźnik do obiektu, który implementuje **IComponent**. Ten parametr jest **NULL** Jeśli powiadomienia nie są przekazywane z **IComponent::Notify**.  
  
 `type`  
 [in] Określa typ obiektu. Może mieć jedną z następujących wartości:  
  
- **CCT_SCOPE** obiektu dla kontekstu zakresu okienka.  
  
- **CCT_RESULT** obiektu dla kontekstu w okienku wyników.  
  
- **CCT_SNAPIN_MANAGER** obiektu dla kontekstu przystawki Menedżer.  
  
- **CCT_UNINITIALIZED** obiekt danych ma nieprawidłowy typ.  
  
##  <a name="querypagesfor"></a>CSnapInItemImpl::QueryPagesFor  
 Wywołuje się, czy węzeł przystawki obsługuje strony właściwości.  
  
```
QueryPagesFor(DATA_OBJECT_TYPES type);
```  
  
##  <a name="setmenuinsertionflags"></a>CSnapInItemImpl::SetMenuInsertionFlags  
 Wywołanie tej funkcji, aby zmodyfikować flagi wstawiania menu, określony przez `pInsertionAllowed`, dla obiekt przystawki.  
  
```
void SetMenuInsertionFlags(  
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```  
  
### <a name="parameters"></a>Parametry  
 *bBeforeInsertion*  
 [in] Różna od zera, jeśli funkcja powinna być wywoływana przed elementy są dodawane do menu kontekstowego; w przeciwnym razie 0.  
  
 `pInsertionAllowed`  
 [w, out] Identyfikuje zdefiniowane konsoli programu MMC, element menu wstawiania punkty, które mogą być używane. Może to być kombinacją następujące flagi:  
  
- **CCM_INSERTIONALLOWED_TOP** elementy mogą być wstawiane w górnej części menu kontekstowego.  
  
- **CCM_INSERTIONALLOWED_NEW** można wstawiać elementy podmenu Utwórz nowy.  
  
- **CCM_INSERTIONALLOWED_TASK** można wstawiać elementy w menu zadania.  
  
- **CCM_INSERTIONALLOWED_VIEW** można wstawiać elementy w menu Widok paska narzędzi lub w podmenu Widok z menu kontekstowe okienka wyników.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli tworzysz Przystawka podstawowa, można zresetować żadnego flagi wstawiania sposób ograniczenia rodzaj elementów menu, które można dodać rozszerzenia innych firm. Na przykład Przystawka podstawowa można wyczyścić **CCM_INSERTIONALLOWED_NEW** flagę, aby zapobiec dodaniu własnych tworzenie nowych elementów menu rozszerzenia.  
  
 Nie należy próbować ustawiać bitów `pInsertionAllowed` które pierwotnie zostały wyczyszczone. Przyszłych wersjach programu MMC może używać usługi bits nie jest obecnie zdefiniowane, nie należy zmieniać bitów, które aktualnie jest niezdefiniowana.  
  
##  <a name="settoolbarbuttoninfo"></a>CSnapInItemImpl::SetToolbarButtonInfo  
 Wywołanie tej funkcji, aby zmodyfikować styl do przycisku paska narzędzi, obiektu przystawki przed utworzeniem pasku narzędzi.  
  
```
void SetToolbarButtonInfo(  
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [in] Identyfikator przycisku paska narzędzi do ustawienia.  
  
 `fsState`  
 [in] Flagi stanu przycisku. Może to być jeden lub więcej z następujących czynności:  
  
- `TBSTATE_CHECKED`Przycisk ma **TBSTYLE_CHECKED** styl i Trwa naciśnięciu.  
  
- `TBSTATE_ENABLED`Przycisk akceptuje dane wejściowe użytkownika. Przycisk, którego nie ma w tym stanie nie akceptuje dane wejściowe użytkownika i jest niedostępny.  
  
- `TBSTATE_HIDDEN`Przycisk nie jest widoczny i nie może odbierać dane wejściowe użytkownika.  
  
- `TBSTATE_INDETERMINATE`Ten przycisk jest niedostępny.  
  
- `TBSTATE_PRESSED`Przycisk jest naciśnięty.  
  
- `TBSTATE_WRAP`Podział wiersza jest zgodna przycisku. Przycisk musi mieć również `TBSTATE_ENABLED`.  
  
 *fsType*  
 [in] Flagi stanu przycisku. Może to być jeden lub więcej z następujących czynności:  
  
- `TBSTYLE_BUTTON`Tworzy standardowe przycisku.  
  
- `TBSTYLE_CHECK`Tworzy stanów naciśniętego i naciśnięciu nie zawsze kliknięcie przycisku. Przycisk ma inny kolor tła, gdy jest on w stan naciśnięcia.  
  
- `TBSTYLE_CHECKGROUP`Tworzy przycisk wyboru, która pozostaje wciśnięty, dopóki nie zostanie naciśnięty przycisk innej grupy.  
  
- `TBSTYLE_GROUP`Tworzy przycisk, który pozostaje wciśnięty, dopóki nie zostanie naciśnięty przycisk innej grupy.  
  
- `TBSTYLE_SEP`Tworzy separatora, zapewniając mały odstęp między grupami przycisku. Przycisk, który ma tego stylu nie otrzymuje dane wejściowe użytkownika.  
  
##  <a name="updatemenustate"></a>CSnapInItemImpl::UpdateMenuState  
 Wywołanie tej funkcji można zmodyfikować elementu menu, zanim zostanie wstawiony do menu kontekstowego obiektu przystawki.  
  
```
void UpdateMenuState(  
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [in] Identyfikator elementu menu ma zostać ustawiona.  
  
 `pBuf`  
 [in] Wskaźnik do ciągu dla elementu menu aktualizacji.  
  
 `flags`  
 [in] Określa nowe flagi stanu. Może to być kombinacją następujące flagi:  
  
- **MF_POPUP** Określa, że jest podmenu w menu kontekstowym. Elementy menu, punkty wstawienia i dalsze podmenu mogą być dodane do tego podmenu przy użyciu jego **lCommandID** jako ich **IInsertionPointID**.  
  
- **MF_BITMAP** i `MF_OWNERDRAW` te flagi są niedozwolone i spowoduje zwracana wartość `E_INVALIDARG`.  
  
- **MF_SEPARATOR** rysuje linię podziału poziomą. Tylko **IContextMenuProvider** można dodawać elementów menu z **MF_SEPARATOR** ustawiony.  
  
- **MF_CHECKED** umieszcza znacznik wyboru obok elementu menu.  
  
- **MF_DISABLED** wyłącza element menu, więc nie można wybrać, ale flaga nie jest szary go.  
  
- `MF_ENABLED`Umożliwia element menu, dlatego można ją wybrać, przywracania jej z wyszarzonymi polami stanu.  
  
- **MF_GRAYED** wyłącza element menu graying go, więc nie może być zaznaczone.  
  
- **MF_MENUBARBREAK** działa tak samo, jak **MF_MENUBREAK** flagi na pasku menu. Menu rozwijanego, podmenu lub menu skrótów nowej kolumny, która jest oddzielony od starego kolumny w linii pionowej.  
  
- **MF_MENUBREAK** element zostanie umieszczone w nowym wierszu (na pasku menu) lub w nowej kolumnie bez oddzielające kolumnami (dla menu rozwijanego, podmenu lub menu skrótów).  
  
- **MF_UNCHECKED** nie zaznacz pole wyboru obok elementu (ustawienie domyślne).  
  
 Nie można jednocześnie używać flag następujących grup:  
  
- **MF_DISABLED**, `MF_ENABLED`, i **MF_GRAYED**.  
  
- **MF_MENUBARBREAK** i **MF_MENUBREAK**.  
  
- **MF_CHECKED** i **MF_UNCHECKED**.  
  
##  <a name="updatetoolbarbutton"></a>CSnapInItemImpl::UpdateToolbarButton  
 Wywołanie tej funkcji, aby zmodyfikować przycisku paska narzędzi, obiektu przystawki, przed wyświetleniem.  
  
```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 Określa identyfikator przycisku przycisku paska narzędzi do aktualizacji.  
  
 `fsState`  
 Określa stan przycisku paska narzędzi. Jeśli ten stan jest określone, zwróć **TRUE**. Może to być kombinacją następujące flagi:  
  
- **WŁĄCZONE** przycisku akceptuje dane wejściowe użytkownika. Przycisk, którego nie ma w tym stanie nie akceptuje dane wejściowe użytkownika i jest niedostępny.  
  
- **ZAZNACZONE** ma przycisk **zaznaczone** styl i Trwa naciśnięciu.  
  
- **UKRYTY** przycisk nie jest widoczny i nie może odbierać dane wejściowe użytkownika.  
  
- **Nieokreślony** przycisk jest niedostępny.  
  
- **BUTTONPRESSED** kliknięciu przycisku.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
