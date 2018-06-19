---
title: Klasa COleDropSource | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDropSource
- AFXOLE/COleDropSource
- AFXOLE/COleDropSource::COleDropSource
- AFXOLE/COleDropSource::GiveFeedback
- AFXOLE/COleDropSource::OnBeginDrag
- AFXOLE/COleDropSource::QueryContinueDrag
dev_langs:
- C++
helpviewer_keywords:
- COleDropSource [MFC], COleDropSource
- COleDropSource [MFC], GiveFeedback
- COleDropSource [MFC], OnBeginDrag
- COleDropSource [MFC], QueryContinueDrag
ms.assetid: d3eecc5f-a70b-4a01-b705-7d2c098ebe17
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e510811fcaac81aa54699250ef37f48ffe1f40e2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374900"
---
# <a name="coledropsource-class"></a>Klasa COleDropSource
Umożliwia danych przeciąganych do miejsca docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleDropSource : public CCmdTarget  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleDropSource::COleDropSource](#coledropsource)|Konstruuje `COleDropSource` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleDropSource::GiveFeedback](#givefeedback)|Kursor zmienia się podczas operacji przeciągania i upuszczania.|  
|[COleDropSource::OnBeginDrag](#onbegindrag)|Obsługuje przechwytywanie myszy podczas operacji przeciągania i upuszczania.|  
|[COleDropSource::QueryContinueDrag](#querycontinuedrag)|Sprawdza, czy przeciąganie powinno być kontynuowane.|  
  
## <a name="remarks"></a>Uwagi  
 [COleDropTarget](../../mfc/reference/coledroptarget-class.md) klasa obsługuje odbierania część operacji przeciągania i upuszczania. `COleDropSource` Obiektu jest odpowiedzialny za określenie, kiedy rozpoczyna się operacja przeciągania, przekazywanie opinii podczas operacji przeciągania i określania, kiedy kończy się operacja przeciągania.  
  
 Aby użyć `COleDropSource` obiektów, po prostu Wywołaj konstruktora. Upraszcza proces określania, jakie zdarzenia, takie jak kliknięcie myszą rozpocząć operację przeciągania przy użyciu [COleDataSource::DoDragDrop](../../mfc/reference/coledatasource-class.md#dodragdrop), [COleClientItem::DoDragDrop](../../mfc/reference/coleclientitem-class.md#dodragdrop), lub [ COleServerItem::DoDragDrop](../../mfc/reference/coleserveritem-class.md#dodragdrop) funkcji. Te funkcje będą Utwórz `COleDropSource` obiekt. Należy zmodyfikować domyślne zachowanie `COleDropSource` funkcje z możliwością zastąpienia. Te funkcje Członkowskie zostanie wywołana w odpowiednim czasie przez platformę.  
  
 Aby uzyskać więcej informacji na temat operacji przeciągania i upuszczania za pomocą mechanizmu OLE, zobacz artykuł [przeciąganie i upuszczanie (OLE)](../../mfc/drag-and-drop-ole.md).  
  
 Aby uzyskać więcej informacji, zobacz [IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071) w zestawie Windows SDK.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropSource`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxole.h  
  
##  <a name="coledropsource"></a>  COleDropSource::COleDropSource  
 Konstruuje `COleDropSource` obiektu.  
  
```  
COleDropSource();
```  
  
##  <a name="givefeedback"></a>  COleDropSource::GiveFeedback  
 Wywoływane przez platformę po wywołaniu [COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover) lub [COleDropTarget::DragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).  
  
```  
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```  
  
### <a name="parameters"></a>Parametry  
 `dropEffect`  
 Efekt, który może zostać wyświetlony dla użytkownika, zwykle wskazujący, co się stanie, jeśli spadek wystąpił w tym punkcie z wybranych danych. Zazwyczaj jest to wartość zwrócona przez wywołanie najnowszych [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter) lub [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover). Można co najmniej jeden z następujących czynności:  
  
- `DROPEFFECT_NONE` Spadek będzie niemożliwe.  
  
- `DROPEFFECT_COPY` Czy można wykonać operacji kopiowania.  
  
- `DROPEFFECT_MOVE` Czy można wykonać operacji przenoszenia.  
  
- `DROPEFFECT_LINK` Czy można ustanowić łącze z porzuconych danych do oryginalnych danych.  
  
- `DROPEFFECT_SCROLL` Operację przeciągania przewijania może nastąpić lub występuje w miejscu docelowym.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **DRAGDROP_S_USEDEFAULTCURSORS** Jeśli przeciąganie jest w toku, **brak błędu** Jeśli nie jest.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji w celu otrzymania opinii dla użytkownika o rezultat spadek wystąpił w tym momencie. Domyślna implementacja używa kursory domyślne OLE. Aby uzyskać więcej informacji na temat operacji przeciągania i upuszczania za pomocą mechanizmu OLE, zobacz artykuł [przeciąganie i upuszczanie (OLE)](../../mfc/drag-and-drop-ole.md).  
  
 Aby uzyskać więcej informacji, zobacz [IDropSource::GiveFeedback](http://msdn.microsoft.com/library/windows/desktop/ms693723), [IDropTarget::DragOver](http://msdn.microsoft.com/library/windows/desktop/ms680129), i [IDropTarget::DragEnter](http://msdn.microsoft.com/library/windows/desktop/ms680106) w zestawie Windows SDK.  
  
##  <a name="onbegindrag"></a>  COleDropSource::OnBeginDrag  
 Wywoływane przez platformę, gdy wystąpi zdarzenie, które można rozpocząć operacji przeciągania, takich jak naciśnięcie przycisku lewego przycisku myszy.  
  
```  
virtual BOOL OnBeginDrag(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Wskazuje okna zawierającego wybrane dane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli przeciąganie jest dozwolone, w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję, jeśli chcesz zmodyfikować sposób uruchomienia procesu przeciągania. Domyślna implementacja przechwytuje mysz i pozostaje w trybie przeciągania, dopóki użytkownik kliknie przycisk myszy do lewego lub prawego lub trafienia ESC, co zwalnia myszy.  
  
##  <a name="querycontinuedrag"></a>  COleDropSource::QueryContinueDrag  
 Po rozpoczęciu przeciągania, ta funkcja jest wywoływana wielokrotnie przez platformę do czasu anulowania lub zakończona operacja przeciągania.  
  
```  
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed, 
    DWORD dwKeyState);
```  
  
### <a name="parameters"></a>Parametry  
 *bEscapePressed*  
 Określają, czy został naciśnięty klawisz ESC od czasu ostatniego wywołania `COleDropSource::QueryContinueDrag`.  
  
 `dwKeyState`  
 Zawiera stan klawisze modyfikujące na klawiaturze. To jest kombinacją dowolną liczbę następujących: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_ MBUTTON**, i **MK_RBUTTON**.  
  
### <a name="return-value"></a>Wartość zwracana  
 **DRAGDROP_S_CANCEL** naciśnięciu klawisza ESC lub prawego przycisku myszy, czy lewego przycisku jest wywoływane przed wykonaniem przeciąganie uruchamia. **DRAGDROP_S_DROP** Jeśli powinna wystąpić operacja przeciągania. W przeciwnym razie `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji, jeśli chcesz zmienić punkt, w których przeciąganie jest anulowana lub spadek występuje.  
  
 Domyślna implementacja inicjuje listy lub Anuluje przeciąganie w następujący sposób. Anuluje operację przeciągania po naciśnięciu klawisza ESC lub prawego przycisku myszy. Inicjuje operacji usuwania podczas lewy przycisk myszy jest wywoływane po rozpoczęciu przeciągania. W przeciwnym razie zwraca `S_OK` i wykonuje nie dalsze działania.  
  
 Ponieważ ta funkcja jest wywoływana często, powinny być optymalizowane możliwie.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC HIERSVR](../../visual-cpp-samples.md)   
 [Przykładowe MFC OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget — klasa](../../mfc/reference/ccmdtarget-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



