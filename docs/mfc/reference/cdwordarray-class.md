---
title: Klasa CDWordArray | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDWordArray
- AFXCOLL/CDWordArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
dev_langs: C++
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: 581be11e-ced6-47d1-8679-e0b8e7d99494
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d99942bf039811db8299e3f6bc6a8c52e3026b68
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdwordarray-class"></a>Klasa CDWordArray
Obsługuje tablic doublewords 32-bitowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDWordArray : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
 Funkcje Członkowskie `CDWordArray` są podobne do funkcji Członkowskich klasy [CObArray](../../mfc/reference/cobarray-class.md). Ze względu na to podobieństwa, można użyć `CObArray` odwołania dokumentacji charakterystykę funkcja elementu członkowskiego. Po wyświetleniu `CObject` wskaźnika jako parametr funkcji lub wartości zwracanej, Zastąp `DWORD`.  
  
 `CObject* CObArray::GetAt( int <nIndex> ) const;`  
  
 na przykład umożliwia to  
  
 `DWORD CDWordArray::GetAt( int <nIndex> ) const;`  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CObArray::CObArray](../../mfc/reference/cobarray-class.md#cobarray)|Tworzy pustą tablicę.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CObArray::Add](../../mfc/reference/cobarray-class.md#add)|Dodaje element do końca tablicy; Jeśli to konieczne, zwiększa rozmiar tablicy.|  
|[CObArray::Append](../../mfc/reference/cobarray-class.md#append)|Dołącza innej tablicy do tablicy; Jeśli to konieczne, zwiększa rozmiar tablicy.|  
|[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)|Kopiuje innej tablicy do tablicy; Jeśli to konieczne, zwiększa rozmiar tablicy.|  
|[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Zwraca tymczasowego odwołanie do typu byte w tablicy.|  
|[CObArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Zwalnia wszystkie nieużywanej pamięci powyżej bieżącego górną granicę.|  
|[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Zwraca wartość pod danym indeksem.|  
|[CObArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|Pobiera liczbę elementów w tej macierzy.|  
|[CObArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Umożliwia dostęp do elementów w tablicy. Może być **NULL**.|  
|[CObArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|Pobiera liczbę elementów w tej macierzy.|  
|[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Zwraca największy nieprawidłowy indeks.|  
|[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Wstawia elementu (lub wszystkie elementy w innej tablicy) od określonego indeksu.|  
|[CObArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Określa, czy tablica jest pusta.|  
|[CObArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Usuwa wszystkie elementy z tej tablicy.|  
|[CObArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Usuwa element pod określonym indeksem.|  
|[CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Ustawia wartość dla danego indeksu; Tablica nie może wzrosnąć.|  
|[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Ustawia wartość dla danego indeksu; Jeśli to konieczne, zwiększa rozmiar tablicy.|  
|[CObArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|Ustawia liczbę elementów, które mają zostać zawarte w tej macierzy.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[[CObArray::operator]](../../mfc/reference/cobarray-class.md#operator_at)|Ustawia lub pobiera element pod określonym indeksem.|  
  
## <a name="remarks"></a>Uwagi  
 `CDWordArray`zawiera `IMPLEMENT_SERIAL` makro do obsługi serializacji i zrzucanie swoich elementów. Jeśli tablica doublewords jest przechowywany w archiwum, za pomocą przeciążenia wstawiania (  **<<** ) — operator lub `Serialize` funkcji członkowskiej, każdy element jest, więc serializacji.  
  
> [!NOTE]
>  Przed rozpoczęciem korzystania z tablicy, użyj `SetSize` jego rozmiar i przydzielić pamięci dla niego. Jeśli nie używasz `SetSize`, dodawanie elementów do macierzy powoduje jego przydzielić często i skopiować. Częste zmiany alokacji i kopiowanie są mało wydajne i można fragmentu pamięci.  
  
 Dane wyjściowe z poszczególnych elementów w tablicy muszą debugowania, należy ustawić głębokość `CDumpContext` obiekt do 1 lub większą.  
  
 Aby uzyskać więcej informacji na temat używania `CDWordArray`, zapoznaj się z artykułem [kolekcji](../../mfc/collections.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcoll.h  
  
## <a name="see-also"></a>Zobacz też  
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CObArray](../../mfc/reference/cobarray-class.md)
