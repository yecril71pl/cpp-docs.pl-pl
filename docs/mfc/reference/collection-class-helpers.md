---
title: Pomocnicy klasy kolekcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- DestructElements function
- ConstructElements function
- SerializeElements function
- collection classes [MFC], helper functions
- helper functions collection class [MFC]
ms.assetid: bc3a2368-9edd-4748-9e6a-13cba79517ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d00d78acf7ddf8cfa27e117cbcdbbb00c7d6fa6b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="collection-class-helpers"></a>Pomocnicy klasy kolekcji
Klasy kolekcji `CMap`, `CList`, i `CArray` za pomocą funkcji opartego na szablonie globalne pomocnika do celów takich jak porównywanie, kopiowanie i elementy serializacji. Jako część implementacji klasy na podstawie `CMap`, `CList`, i `CArray`, konieczne jest przesłonięcie tych funkcji w razie potrzeby z wersjami dostosowane do typu danych przechowywanych w mapie, listy lub tablicy. Aby uzyskać informacje dotyczące zastępowania takich jak funkcje pomocnicze `SerializeElements`, zapoznaj się z artykułem [kolekcje: porady: tworzenie bezpiecznej kolekcji](../../mfc/how-to-make-a-type-safe-collection.md). Należy pamiętać, że **constructelements —** i **destructelements —** są przestarzałe.  
  
 Microsoft Foundation Class Library zapewnia następujące funkcje globalne w afxtempl.h do dostosowywania klas kolekcji:  
  
### <a name="collection-class-helpers"></a>Pomocnicy klasy kolekcji  
  
|||  
|-|-|  
|[Compareelements —](#compareelements)|Wskazuje, czy elementy są takie same.|  
|[Copyelements —](#copyelements)|Kopiuje elementy z jedną tablicą do innego.|  
|[Dumpelements —](#dumpelements)|Udostępnia zorientowane na strumienia diagnostycznych danych wyjściowych.|  
|[HashKey](#hashkey)|Oblicza klucza mieszającego.|  
|[Serializeelements —](#serializeelements)|Przechowuje i pobiera elementy do lub z archiwum.|  
  
##  <a name="compareelements"></a>  Compareelements —  
 Wywoływana bezpośrednio przez [CList::Find] (class.md clist — #not_found.md #clist__find i pośrednio przez [cmap__lookup](cmap-class.md#lookup) i [cmap__operator &#91; &#93; ](cmap-class.md#operator_at).  
  
```   
template<class TYPE, class ARG_TYPE>  
BOOL AFXAPI  
CompareElements(
    const TYPE* pElement1,  
    const ARG_TYPE* pElement2);  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Typ pierwszego elementu ma być porównywana.  
  
 `pElement1`  
 Wskaźnik do pierwszego elementu ma być porównywana.  
  
 `ARG_TYPE`  
 Typ drugiego elementu ma być porównywana.  
  
 `pElement2`  
 Wskaźnik do drugiego elementu ma być porównywana.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli obiekt wskazywany przez `pElement1` jest taki sam obiekt wskazywany przez `pElement2`; w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 `CMap` Wymaga użycia `CMap` parametrów szablonu *klucza* i `ARG_KEY`.  
  
 Domyślna implementacja zwraca wynik porównania  *\*pElement1* i  *\*pElement2*. Należy przesłonić tę funkcję, dzięki czemu porównuje elementów w taki sposób, który jest odpowiedni dla twojej aplikacji.  
  
 Operator porównania definiuje języka C++ ( `==`) dla typów prostych ( `char`, `int`, **float**i tak dalej), ale nie definiuje operator porównania dla klas i struktur. Jeśli chcesz użyć `CompareElements` lub można utworzyć wystąpienia jednego z klasy kolekcji, które korzysta z niego, należy zdefiniować operator porównania lub przeciążenia `CompareElements` przy użyciu wersji, która zwraca odpowiednie wartości.  
  
### <a name="requirements"></a>Wymagania  
   **Nagłówek:** afxtempl.h   
  
##  <a name="copyelements"></a>  Copyelements —  
 Ta funkcja jest wywoływana bezpośrednio przez [CArray::Append](carray-class.md#append) i [CArray::Copy](carray-class.md#copy).  
  
```   
template<class TYPE>  
void AFXAPI CopyElements(
    TYPE* pDest,  
    const TYPE* pSrc,  
    INT_PTR nCount);  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr szablonu określający typ elementów do skopiowania.  
  
 `pDest`  
 Wskaźnik do miejsca docelowego, do której zostaną skopiowane elementy.  
  
 `pSrc`  
 Wskaźnik do źródła elementów do skopiowania.  
  
 `nCount`  
 Liczba elementów do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja używa operator przypisania prostego ( **=** ) do wykonywania operacji kopiowania. Jeśli typ kopiowania nie jest przeciążony operator =, wykona kopię bitowe w implementacji domyślnej.  
  
 Aby uzyskać informacje dotyczące implementacji to i inne funkcje pomocnicze, zobacz artykuł [kolekcje: porady: tworzenie bezpiecznej kolekcji](../how-to-make-a-type-safe-collection.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxtempl.h  
  
##  <a name="dumpelements"></a>  Dumpelements —  
 Udostępnia zorientowane na strumienia diagnostycznych danych wyjściowych w postaci tekstu dla elementów kolekcji w przypadku przesłonięcia.  
  
```   
template<class TYPE>  
void  AFXAPI DumpElements(
    CDumpContext& dc,  
    const TYPE* pElements,  
    INT_PTR nCount);  
```  
  
### <a name="parameters"></a>Parametry  
 `dc`  
 Zrzut kontekst dla zrzucanie elementów.  
  
 *TYP*  
 Parametr szablonu określający typ elementów.  
  
 `pElements`  
 Wskaźnik do elementy, aby można utworzyć zrzutu.  
  
 `nCount`  
 Liczba elementów do można utworzyć zrzutu.  
  
### <a name="remarks"></a>Uwagi  
 **CArray::Dump**, **CList::Dump**, i **CMap::Dump** wywołania funkcji, to jeśli głębokością zrzutu jest większa niż 0.  
  
 Domyślna implementacja nie działa. Jeśli elementy kolekcji są uzyskiwane z `CObject`, zwykle iteracji zastąpienia przez elementy kolekcji, wywoływania `Dump` dla każdego elementu w ruchu.  
  

### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxtempl.h  
  
##  <a name="hashkey"></a>  HashKey  
 Oblicza wartość skrótu dla danego klucza.  
  
```  
template<class ARG_KEY>  
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key); 
```  
  
### <a name="parameters"></a>Parametry  
 `ARG_KEY`  
 Parametr szablonu określający typ danych używany do dostępu do kluczy mapy.  
  
 `key`  
 Klucz wartości skrótu, którego ma zostać obliczona.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość skrótu klucza.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana bezpośrednio przez [CMap::RemoveKey](cmap-class.md#removekey) i pośrednio przez [CMap::Lookup](cmap-class.md#lookup) i [CMap::Operator &#91; &#93; ](cmap-class.md#operator_at).
  
 Domyślna implementacja tworzy wartość skrótu przy przesunięciu `key` bezpośrednio przez cztery pozycji. Należy przesłonić tę funkcję, dzięki czemu wartości skrótu zwraca odpowiedni dla twojej aplikacji.  
  
### <a name="example"></a>Przykład
 ```cpp  
template <> UINT AFXAPI HashKey(unsigned __int64 key)
{
   // Generate the hash value by XORing the lower 32 bits of the number 
   // with the upper 32 bits
   return(UINT(key) ^ UINT(key >> 32));
}
 ```
 
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxtempl.h 
  
##  <a name="serializeelements"></a>  Serializeelements —  
 [Carray —](carray-class.md), [clist —](clist-class.md), i [CMap](cmap-class.md) wywołanie tej funkcji do serializacji elementów.  
  
```   
template<class TYPE>  
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr szablonu określający typ elementów.  
  
 `ar`  
 Obiekt archiwum archiwizacji lub wejściowych.  
  
 `pElements`  
 Wskaźnik do elementów archiwizowane.  
  
 `nCount`  
 Liczba elementów jest archiwizowany  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja jest bitowej odczytu lub zapisu.  
  
 Aby uzyskać informacje dotyczące implementacji to i inne funkcje pomocnicze, zobacz artykuł [kolekcje: porady: tworzenie bezpiecznej kolekcji](../how-to-make-a-type-safe-collection.md).  
  
### <a name="example"></a>Przykład  
 Zapoznaj się z przykładem w artykule [kolekcje: porady: tworzenie bezpiecznej kolekcji](../how-to-make-a-type-safe-collection.md).  
 
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxtempl.h 
    
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](mfc-macros-and-globals.md)   
 [Klasa CMap](cmap-class.md)   
 [Clist — klasa](clist-class.md)   
 [Klasa CArray](carray-class.md)