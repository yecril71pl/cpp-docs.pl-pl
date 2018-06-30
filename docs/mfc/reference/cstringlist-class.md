---
title: Klasa CStringList | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStringList
- AFXCOLL/CStringList
- AFXCOLL/CObList::CObList
- AFXCOLL/CObList::AddHead
- AFXCOLL/CObList::AddTail
- AFXCOLL/CObList::Find
- AFXCOLL/CObList::FindIndex
- AFXCOLL/CObList::GetAt
- AFXCOLL/CObList::GetCount
- AFXCOLL/CObList::GetHead
- AFXCOLL/CObList::GetHeadPosition
- AFXCOLL/CObList::GetNext
- AFXCOLL/CObList::GetPrev
- AFXCOLL/CObList::GetSize
- AFXCOLL/CObList::GetTail
- AFXCOLL/CObList::GetTailPosition
- AFXCOLL/CObList::InsertAfter
- AFXCOLL/CObList::InsertBefore
- AFXCOLL/CObList::IsEmpty
- AFXCOLL/CObList::RemoveAll
- AFXCOLL/CObList::RemoveAt
- AFXCOLL/CObList::RemoveHead
- AFXCOLL/CObList::RemoveTail
- AFXCOLL/CObList::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CObList [MFC], CObList
- CObList [MFC], AddHead
- CObList [MFC], AddTail
- CObList [MFC], Find
- CObList [MFC], FindIndex
- CObList [MFC], GetAt
- CObList [MFC], GetCount
- CObList [MFC], GetHead
- CObList [MFC], GetHeadPosition
- CObList [MFC], GetNext
- CObList [MFC], GetPrev
- CObList [MFC], GetSize
- CObList [MFC], GetTail
- CObList [MFC], GetTailPosition
- CObList [MFC], InsertAfter
- CObList [MFC], InsertBefore
- CObList [MFC], IsEmpty
- CObList [MFC], RemoveAll
- CObList [MFC], RemoveAt
- CObList [MFC], RemoveHead
- CObList [MFC], RemoveTail
- CObList [MFC], SetAt
ms.assetid: 310a7edb-263c-4bd2-ac43-0bfbfddc5a33
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 31e13222ccd5ac12768961ff5e93d11e68ecfded
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122718"
---
# <a name="cstringlist-class"></a>Klasa CStringList
Obsługuje listy `CString` obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CStringList : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
 Funkcje Członkowskie `CStringList` są podobne do funkcji Członkowskich klasy [CObList](../../mfc/reference/coblist-class.md). Ze względu na to podobieństwa, można użyć `CObList` odwołania dokumentacji charakterystykę funkcja elementu członkowskiego. Po wyświetleniu `CObject` wskaźnika jako wartości zwracane, Zastąp `CString` (nie `CString` wskaźnika). Po wyświetleniu `CObject` wskaźnika jako parametru funkcji, należy zastąpić `LPCTSTR`.  
  
 `CObject*& CObList::GetHead() const;`  
  
 na przykład umożliwia to  
  
 `CString& CStringList::GetHead() const;`  
  
 and  
  
 `POSITION AddHead( CObject* <newElement> );`  
  
 Umożliwia to  
  
 `POSITION AddHead( LPCTSTR <newElement> );`  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)|Tworzy pustą listę.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CObList::AddHead](../../mfc/reference/coblist-class.md#addhead)|Dodaje nagłówek listy (sprawia, że nowe head) elementu (lub wszystkie elementy w innej listy).|  
|[CObList::AddTail](../../mfc/reference/coblist-class.md#addtail)|Dodaje elementu (lub wszystkie elementy w innej listy) do fragmentu listy (sprawia, że nowe fragmentu).|  
|[CObList::Find](../../mfc/reference/coblist-class.md#find)|Pobiera pozycję element określony przez wartość wskaźnika.|  
|[CObList::FindIndex](../../mfc/reference/coblist-class.md#findindex)|Pobiera pozycję element określony przez indeks liczony od zera.|  
|[CObList::GetAt](../../mfc/reference/coblist-class.md#getat)|Pobiera element na określonej pozycji.|  
|[CObList::GetCount](../../mfc/reference/coblist-class.md#getcount)|Zwraca liczbę elementów na tej liście.|  
|[CObList::GetHead](../../mfc/reference/coblist-class.md#gethead)|Zwraca element head listy (nie może być pusta).|  
|[CObList::GetHeadPosition](../../mfc/reference/coblist-class.md#getheadposition)|Zwraca pozycję głównym elementem na liście.|  
|[CObList::GetNext](../../mfc/reference/coblist-class.md#getnext)|Pobiera następnego elementu potrzeby iteracji.|  
|[CObList::GetPrev](../../mfc/reference/coblist-class.md#getprev)|Pobiera poprzedni element potrzeby iteracji.|  
|[CObList::GetSize](../../mfc/reference/coblist-class.md#getsize)|Zwraca liczbę elementów na tej liście.|  
|[CObList::GetTail](../../mfc/reference/coblist-class.md#gettail)|Zwraca element tail listy (nie może być pusta).|  
|[CObList::GetTailPosition](../../mfc/reference/coblist-class.md#gettailposition)|Zwraca pozycję tail elementu listy.|  
|[CObList::InsertAfter](../../mfc/reference/coblist-class.md#insertafter)|Wstawia nowego elementu po określonej pozycji.|  
|[CObList::InsertBefore](../../mfc/reference/coblist-class.md#insertbefore)|Wstawia nowy element przed określonej pozycji.|  
|[CObList::IsEmpty](../../mfc/reference/coblist-class.md#isempty)|Testy dla warunku lista jest pusta (Brak elementów).|  
|[CObList::RemoveAll](../../mfc/reference/coblist-class.md#removeall)|Usuwa wszystkie elementy z tej listy.|  
|[CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat)|Usuwa element z tej listy, określony przez pozycji.|  
|[CObList::RemoveHead](../../mfc/reference/coblist-class.md#removehead)|Usuwa element z listy węzła głównego.|  
|[CObList::RemoveTail](../../mfc/reference/coblist-class.md#removetail)|Usuwa element z tail listy.|  
|[CObList::SetAt](../../mfc/reference/coblist-class.md#setat)|Ustawia element na określonej pozycji.|  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie porównania są realizowane przez wartość, co oznacza, że zamiast adresów ciągów są porównywane znaków w ciągu.  
  
 `CStringList` zawiera implement_serial — makro do obsługi serializacji i zrzucanie swoich elementów. Jeśli lista `CString` obiekty są przechowywane do archiwum z operatorem przeciążone wstawiania lub z `Serialize` wszystkich funkcji członkowskiej `CString` element jest serializowany z kolei.  
  
 Jeśli potrzebujesz zrzutu osoba `CString` elementów, musisz ustawić głębokość kontekstu zrzutu 1 lub większą.  
  
 Aby uzyskać więcej informacji na temat używania `CStringList`, zapoznaj się z artykułem [kolekcji](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CStringList`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcoll.h  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC ZBIERANIE](../../visual-cpp-samples.md)   
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



