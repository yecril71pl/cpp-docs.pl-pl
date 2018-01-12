---
title: Klasa CDragListBox | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDragListBox
- AFXCMN/CDragListBox
- AFXCMN/CDragListBox::CDragListBox
- AFXCMN/CDragListBox::BeginDrag
- AFXCMN/CDragListBox::CancelDrag
- AFXCMN/CDragListBox::Dragging
- AFXCMN/CDragListBox::DrawInsert
- AFXCMN/CDragListBox::Dropped
- AFXCMN/CDragListBox::ItemFromPt
dev_langs: C++
helpviewer_keywords:
- CDragListBox [MFC], CDragListBox
- CDragListBox [MFC], BeginDrag
- CDragListBox [MFC], CancelDrag
- CDragListBox [MFC], Dragging
- CDragListBox [MFC], DrawInsert
- CDragListBox [MFC], Dropped
- CDragListBox [MFC], ItemFromPt
ms.assetid: fee20b42-60ae-4aa9-83f9-5a3d9b96e33b
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 424d9db088aa171bdbca868326eb80144a10704b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cdraglistbox-class"></a>Klasa CDragListBox
Oprócz funkcji pole listy Windows `CDragListBox` klasa umożliwia użytkownikowi Przenieś elementy pola listy, takich jak nazwy plików, w polu listy.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDragListBox : public CListBox  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDragListBox::CDragListBox](#cdraglistbox)|Konstruuje `CDragListBox` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDragListBox::BeginDrag](#begindrag)|Wywoływane przez platformę, gdy rozpoczyna się operacja przeciągania.|  
|[CDragListBox::CancelDrag](#canceldrag)|Wywoływane przez platformę, gdy Anulowano operację przeciągania.|  
|[CDragListBox::Dragging](#dragging)|Wywoływane przez platformę w czasie trwania operacji przeciągania.|  
|[CDragListBox::DrawInsert](#drawinsert)|Rysuje prowadnicę wstawiania, przeciągnij pola listy.|  
|[CDragListBox::Dropped](#dropped)|Wywoływane przez platformę po upuszczeniu elementu.|  
|[CDragListBox::ItemFromPt](#itemfrompt)|Zwraca współrzędne przeciąganie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Pola listy z tej możliwości użytkownicy kolejność elementów na liście w jakikolwiek sposób najbardziej przydaje się do nich. Domyślnie pole listy będzie Przenieś element do nowej lokalizacji na liście. Jednak `CDragListBox` obiektów można dostosować, aby skopiować elementy zamiast przenoszenia.  
  
 Pole listy skojarzony z `CDragListBox` klasy nie mogą mieć **lbs_sort —** lub **LBS_MULTIPLESELECT** stylu. Opis elementu Style pola listy, zobacz [style pola listy](../../mfc/reference/styles-used-by-mfc.md#list-box-styles).  
  
 Aby użyć przeciągnij pole listy w oknie dialogowym istniejących aplikacji, Dodaj pole listy do szablonu okna dialogowego za pomocą edytora okien dialogowych, a następnie przypisz zmienną członkowską (kategorii `Control` i typu zmienną `CDragListBox`) odpowiadającego pola listy kontrolowanie w szablonie okna dialogowego.  
  
 Aby uzyskać więcej informacji na przypisywanie formanty ze zmiennymi Członkowskimi, zobacz [skrót do definiowania zmiennych Członkowskich dla formantów okna dialogowego](../../windows/defining-member-variables-for-dialog-controls.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Clistbox —](../../mfc/reference/clistbox-class.md)  
  
 `CDragListBox`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmn.h  
  
##  <a name="begindrag"></a>CDragListBox::BeginDrag  
 Wywoływane przez platformę, gdy wystąpi zdarzenie, które można rozpocząć operacji przeciągania, takich jak naciśnięcie przycisku lewego przycisku myszy.  
  
```  
virtual BOOL BeginDrag(CPoint pt);
```  
  
### <a name="parameters"></a>Parametry  
 `pt`  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) obiekt, który zawiera współrzędne przeciąganie elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli przeciąganie jest dozwolone, w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję, jeśli chcesz kontrolować, co się dzieje, gdy rozpocznie się wykonywanie operacji przeciągania. Domyślna implementacja przechwytuje mysz i pozostaje w trybie przeciągania, dopóki użytkownik kliknie przycisk myszy do lewego lub prawego lub naciśnie klawisz ESC, po tym czasie operacja przeciągania została anulowana.  
  
##  <a name="canceldrag"></a>CDragListBox::CancelDrag  
 Wywoływane przez platformę, gdy Anulowano operację przeciągania.  
  
```  
virtual void CancelDrag(CPoint pt);
```  
  
### <a name="parameters"></a>Parametry  
 `pt`  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) obiekt, który zawiera współrzędne przeciąganie elementu.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji do obsługi dowolnej specjalnego przetwarzania dla formantu pole listy.  
  
##  <a name="cdraglistbox"></a>CDragListBox::CDragListBox  
 Konstruuje `CDragListBox` obiektu.  
  
```  
CDragListBox();
```  
  
##  <a name="dragging"></a>CDragListBox::Dragging  
 Wywoływane przez platformę, gdy wewnątrz przeciągania elementu pola listy `CDragListBox` obiektu.  
  
```  
virtual UINT Dragging(CPoint pt);
```  
  
### <a name="parameters"></a>Parametry  
 `pt`  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) obiekt, który zawiera x i y ekranu współrzędne kursora.  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator zasobu kursora do wyświetlenia. Możliwe są następujące wartości:  
  
- `DL_COPYCURSOR`Wskazuje, że zostanie skopiowany element.  
  
- `DL_MOVECURSOR`Wskazuje, że element ma zostać przeniesiona.  
  
- `DL_STOPCURSOR`Wskazuje, czy bieżący element docelowy upuszczania nie jest akceptowane.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca domyślne zachowanie `DL_MOVECURSOR`. Należy przesłonić tę funkcję, jeśli chcesz zapewnić dodatkowe funkcje.  
  
##  <a name="drawinsert"></a>CDragListBox::DrawInsert  
 Wywoływane przez platformę, by narysować prowadnicę wstawiania przed elementem o wskazanym indeksie.  
  
```  
virtual void DrawInsert(int nItem);
```  
  
### <a name="parameters"></a>Parametry  
 `nItem`  
 Liczony od zera indeks punktu wstawiania.  
  
### <a name="remarks"></a>Uwagi  
 Wartość - 1 spowoduje wyczyszczenie prowadnicę wstawiania. Należy przesłonić tę funkcję, aby zmodyfikować wygląd i zachowanie prowadnicę wstawiania.  
  
##  <a name="dropped"></a>CDragListBox::Dropped  
 Wywoływane przez platformę, gdy element zostanie porzucony w `CDragListBox` obiektu.  
  
```  
virtual void Dropped(
    int nSrcIndex,  
    CPoint pt);
```  
  
### <a name="parameters"></a>Parametry  
 *nSrcIndex*  
 Określa liczony od zera indeks porzuconych ciągu.  
  
 `pt`  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) obiekt, który zawiera współrzędne lokacji docelowej.  
  
### <a name="remarks"></a>Uwagi  
 Domyślne zachowanie kopiuje element pole listy i jego danych do nowej lokalizacji, a następnie usunięcie oryginalnego elementu. Należy przesłonić tę funkcję, aby dostosować zachowanie domyślne, np. włączenie kopii elementów pole listy ma zostać przeciągnięty do innych lokalizacji na liście.  
  
##  <a name="itemfrompt"></a>CDragListBox::ItemFromPt  
 Wywołanie tej funkcji można pobrać liczony od zera indeks elementu pola listy znajdującym się w `pt`.  
  
```  
int ItemFromPt(
    CPoint pt,  
    BOOL bAutoScroll = TRUE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pt`  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) obiekt zawierający współrzędne punktu, w polu listy.  
  
 *bAutoScroll*  
 Różna od zera, jeśli przewijanie jest dozwolone, w przeciwnym razie 0.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks elementu pola listy przeciągania.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC TSTCON](../../visual-cpp-samples.md)   
 [Clistbox — klasa](../../mfc/reference/clistbox-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CListBox](../../mfc/reference/clistbox-class.md)
