---
title: Klasa CVSListBox | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CVSListBox
- AFXVSLISTBOX/CVSListBox
- AFXVSLISTBOX/CVSListBox::CVSListBox
- AFXVSLISTBOX/CVSListBox::AddItem
- AFXVSLISTBOX/CVSListBox::EditItem
- AFXVSLISTBOX/CVSListBox::GetCount
- AFXVSLISTBOX/CVSListBox::GetItemData
- AFXVSLISTBOX/CVSListBox::GetItemText
- AFXVSLISTBOX/CVSListBox::GetSelItem
- AFXVSLISTBOX/CVSListBox::RemoveItem
- AFXVSLISTBOX/CVSListBox::SelectItem
- AFXVSLISTBOX/CVSListBox::SetItemData
- AFXVSLISTBOX/CVSListBox::GetListHwnd
dev_langs:
- C++
helpviewer_keywords:
- CVSListBox [MFC], CVSListBox
- CVSListBox [MFC], AddItem
- CVSListBox [MFC], EditItem
- CVSListBox [MFC], GetCount
- CVSListBox [MFC], GetItemData
- CVSListBox [MFC], GetItemText
- CVSListBox [MFC], GetSelItem
- CVSListBox [MFC], RemoveItem
- CVSListBox [MFC], SelectItem
- CVSListBox [MFC], SetItemData
- CVSListBox [MFC], GetListHwnd
ms.assetid: c79be7b4-46ed-4af8-a41e-68962782d8ef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 380b470531fd28d8cfe68aa931105430111c3dbf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cvslistbox-class"></a>Klasa CVSListBox
`CVSListBox` Klasa obsługuje kontrolki edycji listy.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CVSListBox : public CVSListBoxBase  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CVSListBox::CVSListBox](#cvslistbox)|Konstruuje `CVSListBox` obiektu.|  
|`CVSListBox::~CVSListBox`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CVSListBox::AddItem](#additem)|Dodaje ciąg do kontrolki listy. (Przesłania `CVSListBoxBase::AddItem`.)|  
|[CVSListBox::EditItem](#edititem)|Rozpoczyna operację edycji tekstu elementu kontrolki listy. (Przesłania `CVSListBoxBase::EditItem`.)|  
|[CVSListBox::GetCount](#getcount)|Pobiera liczbę ciągów w formancie listy można edytować. (Przesłania `CVSListBoxBase::GetCount`.)|  
|[CVSListBox::GetItemData](#getitemdata)|Pobiera wartość 32-bitowych specyficzne dla aplikacji, która jest skojarzony z elementem kontrolki edycji listy. (Przesłania `CVSListBoxBase::GetItemData`.)|  
|[CVSListBox::GetItemText](#getitemtext)|Pobiera tekst elementu kontrolki edycji listy. (Przesłania `CVSListBoxBase::GetItemText`.)|  
|[CVSListBox::GetSelItem](#getselitem)|Pobiera liczony od zera Indeks aktualnie zaznaczonego elementu w formancie listy można edytować. (Przesłania `CVSListBoxBase::GetSelItem`.)|  
|`CVSListBox::PreTranslateMessage`|Wykonuje translację komunikaty okna przed wysłaniem do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) i [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkcje systemu Windows. Aby uzyskać więcej informacji i składnia metody, zobacz [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Przesłania `CVSListBoxBase::PreTranslateMessage`.)|  
|[CVSListBox::RemoveItem](#removeitem)|Usuwa element z listy można edytować kontrolki. (Przesłania `CVSListBoxBase::RemoveItem`.)|  
|[CVSListBox::SelectItem](#selectitem)|Wybiera ciągu kontrolki edycji listy. (Przesłania `CVSListBoxBase::SelectItem`.)|  
|[CVSListBox::SetItemData](#setitemdata)|Kojarzy specyficzne dla aplikacji 32-bitową wartość z listy można edytować elementu formantu. (Przesłania `CVSListBoxBase::SetItemData`.)|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CVSListBox::GetListHwnd](#getlisthwnd)|Zwraca dojście do bieżącego formantu widoku listy osadzonych.|  
  
## <a name="remarks"></a>Uwagi  
 `CVSListBox` Klasa zawiera zestaw przycisków edycji, które umożliwiają użytkownikowi tworzyć, modyfikować, usuwać ani zmieniać kolejności elementów w formancie listy.  
  
 Poniżej znajduje się obraz kontrolki edycji listy. Drugi wpis listy, który ma nazwę "Item2", został wybrany do edycji.  
  
 ![Formant CVSListBox](../../mfc/reference/media/cvslistbox.png "cvslistbox")  
  
 Jeśli używasz edytora zasobów można dodać kontrolkę listy można edytować, zwróć uwagę, że **przybornika** okienku Edytora nie zawiera formantu wstępnie zdefiniowanej listy można edytować. Zamiast tego, takich jak dodać statyczną kontrolkę **pole grupy** formantu. Platformę używa kontrolki statycznej jako symbol zastępczy, aby określić rozmiar i położenie kontrolki edycji listy.  
  
 Aby użyć kontrolki edycji listy w szablonie — okno dialogowe, należy zadeklarować `CVSListBox` zmiennej w klasie — okno dialogowe. Do obsługi wymiany danych między zmienną i kontrolki, zdefiniuj `DDX_Control` wpisu makra w `DoDataExchange` metody okna dialogowego. Domyślnie przez kontrolki edycji listy jest tworzony bez przycisków edycji. Umożliwiają dziedziczonej metody CVSListBoxBase::SetStandardButtons przycisków edycji.  
  
 Aby uzyskać więcej informacji, zobacz katalogu przykłady `New Controls` przykładowe pliki Page3.cpp i Page3.h.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CStatic](../../mfc/reference/cstatic-class.md)  
  
 `CVSListBoxBase`  
  
 [CVSListBox](../../mfc/reference/cvslistbox-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxvslistbox.h  
  
##  <a name="additem"></a>  CVSListBox::AddItem  
 Dodaje ciąg do kontrolki listy.  
  
```  
virtual int AddItem(
    const CString& strIext,  
    DWORD_PTR dwData=0,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `strIext`  
 Odwołanie do ciągu.  
  
 [in] `dwData`  
 Specyficzne dla aplikacji 32-bitowa wartość skojarzoną z ciągiem. Wartość domyślna to 0.  
  
 [in] `iIndex`  
 Liczony od zera indeks położenie, w którym będą przechowywane na ciąg. Jeśli `iIndex` parametr ma wartość -1, ten ciąg jest dodawane na końcu listy. Wartość domyślna wynosi -1.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks pozycji ciągu w formancie listy.  
  
### <a name="remarks"></a>Uwagi  
 Użyj [CVSListBox::GetItemData](#getitemdata) metodę, aby pobrać wartość, która jest określona przez `dwData` parametru. Ta wartość może być liczbą całkowitą specyficzne dla aplikacji lub wskaźnik do innych danych.  
  
##  <a name="cvslistbox"></a>  CVSListBox::CVSListBox  
 Konstruuje `CVSListBox` obiektu.  
  
```  
CVSListBox();
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="edititem"></a>  CVSListBox::EditItem  
 Rozpoczyna operację edycji tekstu elementu kontrolki listy.  
  
```  
virtual BOOL EditItem(int iIndex);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `iIndex`  
 Liczony od zera indeks elementu kontrolki listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli operacja edytowania rozpoczyna się pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Użytkownik uruchamia operację edycji, klikając etykietę elementu lub naciskając klawisz **F2** lub **spacja** klucza, gdy element ma fokus.  
  
##  <a name="getcount"></a>  CVSListBox::GetCount  
 Pobiera liczbę ciągów w formancie listy można edytować.  
  
```  
virtual int GetCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w formancie listy.  
  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, że liczba jest jeden większa niż wartość indeksu ostatniego elementu, ponieważ indeks jest liczony od zera.  
  
##  <a name="getitemdata"></a>  CVSListBox::GetItemData  
 Pobiera wartość 32-bitowych specyficzne dla aplikacji, która jest skojarzony z elementem kontrolki edycji listy.  
  
```  
virtual DWORD_PTR GetItemData(int iIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] `iIndex`  
 Liczony od zera indeks elementu kontrolki edycji listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 32-bitową wartość skojarzoną z określonym elementem.  
  
### <a name="remarks"></a>Uwagi  
 Użyj [CVSListBox::SetItemData](#setitemdata) lub [CVSListBox::AddItem](#additem) do kojarzenia 32-bitową wartość z listy element kontroli. Ta wartość może być liczbą całkowitą specyficzne dla aplikacji lub wskaźnik do innych danych.  
  
##  <a name="getitemtext"></a>  CVSListBox::GetItemText  
 Pobiera tekst elementu kontrolki edycji listy.  
  
```  
virtual CString GetItemText(int iIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] `iIndex`  
 Liczony od zera indeks elementu kontrolki edycji listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) obiekt, który zawiera tekst określony element.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getlisthwnd"></a>  CVSListBox::GetListHwnd  
 Zwraca dojście do bieżącego formantu widoku listy osadzonych.  
  
```  
virtual HWND GetListHwnd() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do formantu widoku listy osadzonych.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda służy do pobrania dojścia do formantu widoku listy osadzone, który obsługuje `CVSListBox` klasy.  
  
##  <a name="getselitem"></a>  CVSListBox::GetSelItem  
 Pobiera liczony od zera Indeks aktualnie zaznaczonego elementu w formancie listy można edytować.  
  
```  
virtual int GetSelItem() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli ta metoda zakończy się pomyślnie, liczony od zera Indeks aktualnie zaznaczonego elementu; w przeciwnym razie wartość -1.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="removeitem"></a>  CVSListBox::RemoveItem  
 Usuwa element z listy można edytować kontrolki.  
  
```  
virtual BOOL RemoveItem(int iIndex);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `iIndex`  
 Liczony od zera indeks elementu kontrolki edycji listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli określony element jest usunięty; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="selectitem"></a>  CVSListBox::SelectItem  
 Wybiera ciągu kontrolki edycji listy.  
  
```  
virtual BOOL SelectItem(int iItem);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `iItem`  
 Liczony od zera indeks elementu kontrolki edycji listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wybiera określony element i w razie potrzeby, przewinąć element w celu wyświetlenia.  
  
##  <a name="setitemdata"></a>  CVSListBox::SetItemData  
 Kojarzy specyficzne dla aplikacji 32-bitową wartość z listy można edytować elementu formantu.  
  
```  
virtual void SetItemData(
    int iIndex,  
    DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `iIndex`  
 Liczony od zera indeks elementu kontrolki edycji listy.  
  
 [in] `dwData`  
 32-bitowa wartość. Ta wartość może być liczbą całkowitą specyficzne dla aplikacji lub wskaźnik do innych danych.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)
