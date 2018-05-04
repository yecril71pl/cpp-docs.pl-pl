---
title: Klasa CAutoPtr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoPtr
- ATLBASE/ATL::CAutoPtr
- ATLBASE/ATL::CAutoPtr::CAutoPtr
- ATLBASE/ATL::CAutoPtr::Attach
- ATLBASE/ATL::CAutoPtr::Detach
- ATLBASE/ATL::CAutoPtr::Free
- ATLBASE/ATL::CAutoPtr::m_p
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtr class
ms.assetid: 08988d53-4fb0-4711-bdfc-8ac29c63f410
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: edf1baff50541dd5f16c27205f300558558d6f92
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="cautoptr-class"></a>Klasa CAutoPtr
Ta klasa reprezentuje obiekt wskaźnika inteligentnego.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <typename T>  
class CAutoPtr
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ wskaźnika.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAutoPtr::CAutoPtr](#cautoptr)|Konstruktor.|  
|[CAutoPtr:: ~ CAutoPtr](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAutoPtr::Attach](#attach)|Wywołaj tę metodę, aby przejąć na własność istniejącego wskaźnika.|  
|[CAutoPtr::Detach](#detach)|Wywołanie tej metody, aby zwolnić własność wskaźnika.|  
|[CAutoPtr::Free](#free)|Wywołanie tej metody, aby usunąć obiekt wskazywany przez `CAutoPtr`.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAutoPtr::operator T *](#operator_t_star)|Operator rzutowania.|  
|[CAutoPtr::operator =](#operator_eq)|Operator przypisania.|  
|[CAutoPtr::operator ->](#operator_ptr)|Operator wskaźnika do elementu członkowskiego.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAutoPtr::m_p](#m_p)|Zmienna elementu członkowskiego danych wskaźnika.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa dostarcza metody do tworzenia i zarządzania wskaźnika inteligentnego, co pomoże zapewnić ochronę przed przecieki pamięci przez automatycznie zwolnić zasobów, gdy znajduje się poza zakresem.  
  
 Dalsze, `CAutoPtr`Konstruktor kopiujący i przypisania operator przeniesienia własności wskaźnika, kopiowanie źródła wskaźnik na wskaźnik docelowego i ustawienie wartości NULL wskaźnika źródła. W związku z tym nie jest możliwe dwa `CAutoPtr` obiekty każdego przechowywania tego samego wskaźnika i zmniejsza możliwości usunięcia tego samego wskaźnika dwa razy.  
  
 `CAutoPtr` upraszcza tworzenie kolekcji wskaźników. Zamiast tworzenia klasy pochodnej klasy kolekcji i zastępowanie destruktor, jest łatwiejsze tworzenie kolekcji z `CAutoPtr` obiektów. Usunięcie kolekcji `CAutoPtr` obiekty będą się znaleźć poza zakresem i automatycznie usunąć siebie.  
  
 [CHeapPtr](../../atl/reference/cheapptr-class.md) i wariantów działać w taki sam sposób jak `CAutoPtr`, ale przydzielić i zwolnić pamięć, przy użyciu funkcji różnych sterty zamiast C++ **nowe** i **usunąć** operatorów. [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md) jest podobny do `CAutoPtr`, jedyną różnicą jest, że używa **wektorów new []** i **wektor delete []** można przydzielić i zwolnić pamięć.  
  
 Zobacz też [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) i [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) gdy tablice lub list wskaźniki inteligentne są wymagane.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
## <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]  
  
##  <a name="attach"></a>  CAutoPtr::Attach  
 Wywołaj tę metodę, aby przejąć na własność istniejącego wskaźnika.  
  
```
void Attach(T* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 `CAutoPtr` Obiektu będzie przejąć na własność ten wskaźnik.  
  
### <a name="remarks"></a>Uwagi  
 Gdy `CAutoPtr` obiektu przejmuje wskaźnik, automatycznie usunie wskaźnik i przydzielone dane podczas przechodzi ona poza zakresem. Jeśli [CAutoPtr::Detach](#detach) jest wywoływana, programistę jest ponownie podany odpowiedzialność za wszelkie zwalnianie przydzielone zasoby.  
  
 W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli [CAutoPtr::m_p](#m_p) element członkowski danych wskazuje obecnie istniejącej wartości; oznacza to, że nie jest równa NULL.  
  
### <a name="example"></a>Przykład  
 Zapoznaj się z przykładem w [omówienie CAutoPtr](../../atl/reference/cautoptr-class.md).  
  
##  <a name="cautoptr"></a>  CAutoPtr::CAutoPtr  
 Konstruktor.  
  
```
CAutoPtr() throw();
explicit CAutoPtr(T* p) throw();

template<typename TSrc>
CAutoPtr(CAutoPtr<TSrc>& p) throw();

template<> 
CAutoPtr(CAutoPtr<T>& p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Istniejącego wskaźnika.  
  
 `TSrc`  
 Typ zarządzany przez inną `CAutoPtr`używane do zainicjowania bieżącego obiektu.  
  
### <a name="remarks"></a>Uwagi  
 `CAutoPtr` Można utworzyć obiektu przy użyciu istniejącego wskaźnika, w którym to przypadku przesyłania własność wskaźnika.  
  
### <a name="example"></a>Przykład  
 Zapoznaj się z przykładem w [omówienie CAutoPtr](../../atl/reference/cautoptr-class.md).  
  
##  <a name="dtor"></a>  CAutoPtr:: ~ CAutoPtr  
 Destruktor.  
  
```
~CAutoPtr() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie zasoby przydzielone. Wywołania [CAutoPtr::Free](#free).  
  
##  <a name="detach"></a>  CAutoPtr::Detach  
 Wywołanie tej metody, aby zwolnić własność wskaźnika.  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca kopię wskaźnika.  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia własność wskaźnik, ustawia [CAutoPtr::m_p](#m_p) danych zmiennej członkowskiej na wartość NULL i zwraca kopię wskaźnika. Po wywołaniu **Detach**, maksymalnie programisty zwolnienia żadnego przydzielany zasobów służącym `CAutoPtr` obiekt może mieć wcześniej zakłada, że reponsibility.  
  
### <a name="example"></a>Przykład  
 Zapoznaj się z przykładem w [omówienie CAutoPtr](../../atl/reference/cautoptr-class.md).  
  
##  <a name="free"></a>  CAutoPtr::Free  
 Wywołanie tej metody, aby usunąć obiekt wskazywany przez `CAutoPtr`.  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Obiekt wskazywany przez `CAutoPtr` zostanie zwolniona i [CAutoPtr::m_p](#m_p) zmiennej elementu członkowskiego danych jest równa NULL.  
  
##  <a name="m_p"></a>  CAutoPtr::m_p  
 Zmienna elementu członkowskiego danych wskaźnika.  
  
```
T* m_p;
```  
  
### <a name="remarks"></a>Uwagi  
 Ta zmienna elementu członkowskiego zawiera informacje wskaźnika.  
  
##  <a name="operator_eq"></a>  CAutoPtr::operator =  
 Operator przypisania.  
  
```
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Wskaźnik.  
  
 `TSrc`  
 Typ klasy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do **CAutoPtr\< T >**.  
  
### <a name="remarks"></a>Uwagi  
 Operator przypisania odłącza `CAutoPtr` obiektu z dowolnym bieżącego wskaźnika i dołącza nowy wskaźnik `p`, w tym miejscu.  
  
### <a name="example"></a>Przykład  
 Zapoznaj się z przykładem w [omówienie CAutoPtr](../../atl/reference/cautoptr-class.md).  
  
##  <a name="operator_ptr"></a>  CAutoPtr::operator-&gt;  
 Operator wskaźnika do elementu członkowskiego.  
  
```
T* operator->() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość [CAutoPtr::m_p](#m_p) zmiennej członka danych.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego operatora, aby wywołać metodę w klasie wskazywana przez `CAutoPtr` obiektu. W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli `CAutoPtr` wskazuje na wartość NULL.  
  
### <a name="example"></a>Przykład  
 Zapoznaj się z przykładem w [omówienie CAutoPtr](../../atl/reference/cautoptr-class.md).  
  
##  <a name="operator_t_star"></a>  CAutoPtr::operator T *  
 Operator rzutowania.  
  
```  
operator T* () const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do typu danych obiektu zdefiniowaną w szablonie klasy.  
  
### <a name="example"></a>Przykład  
 Zapoznaj się z przykładem w [omówienie CAutoPtr](../../atl/reference/cautoptr-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CHeapPtr](../../atl/reference/cheapptr-class.md)   
 [Klasa CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
