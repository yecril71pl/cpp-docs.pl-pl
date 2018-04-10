---
title: Klasa CAutoVectorPtr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::Allocate
- ATLBASE/ATL::CAutoVectorPtr::Attach
- ATLBASE/ATL::CAutoVectorPtr::Detach
- ATLBASE/ATL::CAutoVectorPtr::Free
- ATLBASE/ATL::CAutoVectorPtr::m_p
dev_langs:
- C++
helpviewer_keywords:
- CAutoVectorPtr class
ms.assetid: 0030362b-6bc4-4a47-9b5b-3c3899dceab4
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b01bb9f74793e739ff0930bae070f00cb909dd61
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cautovectorptr-class"></a>Klasa CAutoVectorPtr
Ta klasa reprezentuje obiekt wskaźnika inteligentnego wektora, używając nowego i delete — operatory.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<typename T>  
class CAutoVectorPtr
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ wskaźnika.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAutoVectorPtr::CAutoVectorPtr](#cautovectorptr)|Konstruktor.|  
|[CAutoVectorPtr:: ~ CAutoVectorPtr](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAutoVectorPtr::Allocate](#allocate)|Wywołanie tej metody można przydzielić pamięci wymaganej przez tablicę obiektów wskazywana przez `CAutoVectorPtr`.|  
|[CAutoVectorPtr::Attach](#attach)|Wywołaj tę metodę, aby przejąć na własność istniejącego wskaźnika.|  
|[CAutoVectorPtr::Detach](#detach)|Wywołanie tej metody, aby zwolnić własność wskaźnika.|  
|[CAutoVectorPtr::Free](#free)|Wywołanie tej metody, aby usunąć obiekt wskazywany przez `CAutoVectorPtr`.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAutoVectorPtr::operator T *](#operator_t__star)|Operator rzutowania.|  
|[CAutoVectorPtr::operator =](#operator_eq)|Operator przypisania.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAutoVectorPtr::m_p](#m_p)|Zmienna elementu członkowskiego danych wskaźnika.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa dostarcza metody do tworzenia i zarządzania wskaźnika inteligentnego, co pomoże zapewnić ochronę przed przecieki pamięci przez automatycznie zwolnić zasobów, gdy znajduje się poza zakresem. `CAutoVectorPtr`przypomina `CAutoPtr`, jedyną różnicą, że trwa `CAutoVectorPtr` używa [nowy wektor &#91; &#93;](../../standard-library/new-operators.md#op_new_arr) i [wektorów Usuń &#91; &#93;](../../standard-library/new-operators.md#op_delete_arr) można przydzielić i zwolnić pamięć, a nie C++ **nowe** i **usunąć** operatorów. Zobacz [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) Jeśli klasy kolekcji `CAutoVectorPtr` są wymagane.  

  
 Zobacz [CAutoPtr](../../atl/reference/cautoptr-class.md) przykład za pomocą klasy wskaźnika inteligentnego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="allocate"></a>CAutoVectorPtr::Allocate  
 Wywołanie tej metody można przydzielić pamięci wymaganej przez tablicę obiektów wskazywana przez `CAutoVectorPtr`.  
  
```
bool Allocate(size_t nElements) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nElements`  
 Liczba elementów w tablicy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli pomyślnie jest pamięć przydzielona, false w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli [CAutoVectorPtr::m_p](#m_p) zmiennej członkowskiej wskazuje obecnie istniejącej wartości; oznacza to, że nie jest równa NULL.  
  
##  <a name="attach"></a>CAutoVectorPtr::Attach  
 Wywołaj tę metodę, aby przejąć na własność istniejącego wskaźnika.  
  
```
void Attach(T* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 `CAutoVectorPtr` Obiektu będzie przejąć na własność ten wskaźnik.  
  
### <a name="remarks"></a>Uwagi  
 Gdy `CAutoVectorPtr` obiektu przejmuje wskaźnik, automatycznie usunie wskaźnik i przydzielone dane podczas przechodzi ona poza zakresem. Jeśli [CAutoVectorPtr::Detach](#detach) jest wywoływana, programistę jest ponownie podany odpowiedzialność za wszelkie zwalnianie przydzielone zasoby.  
  
 W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli [CAutoVectorPtr::m_p](#m_p) zmiennej członkowskiej wskazuje obecnie istniejącej wartości; oznacza to, że nie jest równa NULL.  
  
##  <a name="cautovectorptr"></a>CAutoVectorPtr::CAutoVectorPtr  
 Konstruktor.  
  
```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Istniejącego wskaźnika.  
  
### <a name="remarks"></a>Uwagi  
 `CAutoVectorPtr` Można utworzyć obiektu przy użyciu istniejącego wskaźnika, w którym to przypadku przesyłania własność wskaźnika.  
  
##  <a name="dtor"></a>CAutoVectorPtr:: ~ CAutoVectorPtr  
 Destruktor.  
  
```
~CAutoVectorPtr() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie zasoby przydzielone. Wywołania [CAutoVectorPtr::Free](#free).  
  
##  <a name="detach"></a>CAutoVectorPtr::Detach  
 Wywołanie tej metody, aby zwolnić własność wskaźnika.  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca kopię wskaźnika.  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia własność wskaźnik, ustawia [CAutoVectorPtr::m_p](#m_p) zmiennej członkowskiej na wartość NULL i zwraca kopię wskaźnika. Po wywołaniu **Detach**, maksymalnie programisty zwolnienia żadnego przydzielany zasobów służącym `CAutoVectorPtr` obiekt może mieć wcześniej zakłada, że odpowiedzialności.  
  
##  <a name="free"></a>CAutoVectorPtr::Free  
 Wywołanie tej metody, aby usunąć obiekt wskazywany przez `CAutoVectorPtr`.  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Obiekt wskazywany przez `CAutoVectorPtr` zostanie zwolniona i [CAutoVectorPtr::m_p](#m_p) zmiennej członkowskiej jest równa NULL.  
  
##  <a name="m_p"></a>CAutoVectorPtr::m_p  
 Zmienna elementu członkowskiego danych wskaźnika.  
  
```
T* m_p;
```  
  
### <a name="remarks"></a>Uwagi  
 Ta zmienna elementu członkowskiego zawiera informacje wskaźnika.  
  
##  <a name="operator_eq"></a>CAutoVectorPtr::operator =  
 Operator przypisania.  
  
```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Wskaźnik.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do **CAutoVectorPtr\< T >**.  
  
### <a name="remarks"></a>Uwagi  
 Operator przypisania odłącza `CAutoVectorPtr` obiektu z dowolnym bieżącego wskaźnika i dołącza nowy wskaźnik `p`, w tym miejscu.  
  
##  <a name="operator_t__star"></a>CAutoVectorPtr::operator T *  
 Operator rzutowania.  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwraca wskaźnik do typu danych obiektu zdefiniowaną w szablonie klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CAutoPtr](../../atl/reference/cautoptr-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
