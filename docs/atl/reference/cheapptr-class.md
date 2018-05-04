---
title: Klasa CHeapPtr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CHeapPtr
- ATLCORE/ATL::CHeapPtr
- ATLCORE/ATL::CHeapPtr::CHeapPtr
- ATLCORE/ATL::CHeapPtr::Allocate
- ATLCORE/ATL::CHeapPtr::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtr class
ms.assetid: e5c5bfd4-9bf1-4164-8a83-8155fe253454
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a728f84a2eaa3f0138e2b0a95c25f8867c17432e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="cheapptr-class"></a>Klasa CHeapPtr
Klasa wskaźnika inteligentnego wskaźniki stosu zarządzania.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<typename T, class Allocator=CCRTAllocator>  
class CHeapPtr : public CHeapPtrBase<T, Allocator>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ obiektu do zapisania na stosie.  
  
 `Allocator`  
 Klasa alokacji pamięci do użycia.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHeapPtr::CHeapPtr](#cheapptr)|Konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHeapPtr::Allocate](#allocate)|Wywołanie tej metody można przydzielić pamięci na stercie do przechowywania obiektów.|  
|[CHeapPtr::Reallocate](#reallocate)|Wywołaj tę metodę, aby ponownie przydzielić pamięci na stosie.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHeapPtr::operator =](#operator_eq)|Operator przypisania.|  
  
## <a name="remarks"></a>Uwagi  
 `CHeapPtr` jest pochodną [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) i domyślnie używa procedury CRT (w [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)) można przydzielić i zwolnić pamięć. Klasa [CHeapPtrList](../../atl/reference/cheapptrlist-class.md) może zostać użyty do utworzenia listy wskaźniki stosu. Zobacz też [CComHeapPtr](../../atl/reference/ccomheapptr-class.md), który używa procedury alokacji pamięci COM.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)  
  
 `CHeapPtr`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcore.h  
  
##  <a name="allocate"></a>  CHeapPtr::Allocate  
 Wywołanie tej metody można przydzielić pamięci na stercie do przechowywania obiektów.  
  
```
bool Allocate(size_t nElements = 1) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nElements`  
 Liczba elementów używane do obliczania ilość pamięci do przydzielenia. Wartość domyślna to 1.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli pamięć została pomyślnie przydzielone, wartość false w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Program przydzielania procedury służą do zarezerwować wystarczającej ilości pamięci w stercie do przechowywania *nElement* obiektów zdefiniowanych w konstruktorze.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#77](../../atl/codesnippet/cpp/cheapptr-class_1.cpp)]  
  
##  <a name="cheapptr"></a>  CHeapPtr::CHeapPtr  
 Konstruktor.  
  
```
CHeapPtr() throw();
explicit CHeapPtr(T* p) throw();
CHeapPtr(CHeapPtr<T, Allocator>& p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Istniejące wskaźnik stosu lub `CHeapPtr`.  
  
### <a name="remarks"></a>Uwagi  
 Wskaźnik stosu można opcjonalnie utworzyć przy użyciu istniejącego wskaźnika lub `CHeapPtr` obiektu. Jeśli tak, nowe `CHeapPtr` obiektu przyjmuje na siebie odpowiedzialność zarządzania nowy wskaźnik i zasobów.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#78](../../atl/codesnippet/cpp/cheapptr-class_2.cpp)]  
  
##  <a name="operator_eq"></a>  CHeapPtr::operator =  
 Operator przypisania.  
  
```
CHeapPtr<T, Allocator>& operator=(
    CHeapPtr<T, Allocator>& p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Istniejące `CHeapPtr` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do zaktualizowanego `CHeapPtr`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#80](../../atl/codesnippet/cpp/cheapptr-class_3.cpp)]  
  
##  <a name="reallocate"></a>  CHeapPtr::Reallocate  
 Wywołaj tę metodę, aby ponownie przydzielić pamięci na stosie.  
  
```
bool Reallocate(size_t nElements) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nElements`  
 Nowy numer elementów używane do obliczania ilość pamięci do przydzielenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli pamięć została pomyślnie przydzielone, wartość false w przypadku awarii.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#79](../../atl/codesnippet/cpp/cheapptr-class_4.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)   
 [Klasa CCRTAllocator](../../atl/reference/ccrtallocator-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
