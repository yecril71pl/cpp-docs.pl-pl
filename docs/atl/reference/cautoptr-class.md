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
ms.openlocfilehash: 118e303fe176684ea837861ef3855dd6c03fb04e
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881139"
---
# <a name="cautoptr-class"></a>Klasa CAutoPtr
Ta klasa reprezentuje obiekt inteligentnego wskaźnika.  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <typename T>  
class CAutoPtr
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
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
|[CAutoPtr::Attach](#attach)|Wywołaj tę metodę, aby przejąć prawo własności istniejącego wskaźnika.|  
|[CAutoPtr::Detach](#detach)|Wywołaj tę metodę, aby zwolnić własność wskaźnika.|  
|[CAutoPtr::Free](#free)|Wywołaj tę metodę, aby usunąć obiekt wskazywany przez `CAutoPtr`.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAutoPtr::operator T *](#operator_t_star)|Operator rzutowania.|  
|[CAutoPtr::operator =](#operator_eq)|Operator przypisania.|  
|[CAutoPtr::operator ->](#operator_ptr)|Operator wskaźnika do elementu członkowskiego.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAutoPtr::m_p](#m_p)|Zmiennej składowej danych wskaźnika.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa dostarcza metody do tworzenia i zarządzania inteligentny wskaźnik, co pomoże zapewnić ochronę przed przeciekami pamięci przy zwalnianiu zasobów automatycznie, gdy znajduje się poza zakresem.  
  
 Dodatkowo `CAutoPtr`Konstruktor kopiujący i własność transferu operatora przypisania wskaźnika, kopiowanie wskaźnika źródła do wskaźnika docelowego i ustawienie źródła wskaźnika o wartości NULL. W związku z tym nie można mieć dwie `CAutoPtr` obiekty każdego przechowywanie tego samego wskaźnika i zmniejszy to prawdopodobieństwo usunięcia dwa razy ten sam wskaźnik.  
  
 `CAutoPtr` Ponadto ułatwia tworzenie kolekcji wskaźników. Zamiast wyprowadzanie klasy kolekcji, a przy przesłanianiu destruktora, jest łatwiejsze tworzenie kolekcji z `CAutoPtr` obiektów. Usunięcie kolekcji `CAutoPtr` obiekty zostaną wykraczają poza zakres i automatycznie usunięcia użytkownika.  
  
 [CHeapPtr](../../atl/reference/cheapptr-class.md) i wariantów działać w taki sam sposób jak `CAutoPtr`, z tą różnicą, że ich alokują i zwalniają pamięć przy użyciu funkcji sterty różnych zamiast C++ **nowe** i **Usuń** operatorów. [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md) przypomina `CAutoPtr`, jedyną różnicą jest, że używa on **vector new []** i **wektor delete []** do przydzielają i zwalniają pamięć.  
  
 Zobacz też [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) i [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) po tablic lub listy inteligentne wskaźniki są wymagane.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
## <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]  
  
##  <a name="attach"></a>  CAutoPtr::Attach  
 Wywołaj tę metodę, aby przejąć prawo własności istniejącego wskaźnika.  
  
```
void Attach(T* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *p*  
 `CAutoPtr` Obiekt będzie przejęcie na własność ten wskaźnik.  
  
### <a name="remarks"></a>Uwagi  
 Gdy `CAutoPtr` obiektu przejmuje na własność wskaźnika, usługa automatycznie usunie wskaźnika i wszystkie przydzielone dane podczas jego wykracza poza zakres. Jeśli [CAutoPtr::Detach](#detach) jest wywoływana, programisty jest ponownie podany odpowiedzialność za zwalnianie dowolne zasoby przydzielane.  
  
 W kompilacjach do debugowania błędu potwierdzenia wystąpi [CAutoPtr::m_p](#m_p) element członkowski danych pozwala obecnie przejść do istniejącej wartości; oznacza to, że nie jest równa NULL.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład w [Przegląd CAutoPtr](../../atl/reference/cautoptr-class.md).  
  
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
 *p*  
 Istniejącego wskaźnika.  
  
 *TSrc*  
 Typ zarządzany przez inną `CAutoPtr`, który jest używany do zainicjowania bieżący obiekt.  
  
### <a name="remarks"></a>Uwagi  
 `CAutoPtr` Obiekt może być utworzony przy użyciu istniejącego wskaźnika, w którym to przypadku z tym przenosi własność wskaźnika.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład w [Przegląd CAutoPtr](../../atl/reference/cautoptr-class.md).  
  
##  <a name="dtor"></a>  CAutoPtr:: ~ CAutoPtr  
 Destruktor.  
  
```
~CAutoPtr() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie zasoby przydzielone. Wywołania [CAutoPtr::Free](#free).  
  
##  <a name="detach"></a>  CAutoPtr::Detach  
 Wywołaj tę metodę, aby zwolnić własność wskaźnika.  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca kopię wskaźnika.  
  
### <a name="remarks"></a>Uwagi  
 Uwalnia własność wskaźnika, ustawia [CAutoPtr::m_p](#m_p) zmiennej składowej danych na wartość NULL i zwraca kopię wskaźnika. Po wywołaniu `Detach`, do programisty, aby zwolnić dowolne przydzielany zasobów za pośrednictwem którego `CAutoPtr` obiekt może mieć wcześniej zakładaliśmy reponsibility.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład w [Przegląd CAutoPtr](../../atl/reference/cautoptr-class.md).  
  
##  <a name="free"></a>  CAutoPtr::Free  
 Wywołaj tę metodę, aby usunąć obiekt wskazywany przez `CAutoPtr`.  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Obiekt wskazywany przez `CAutoPtr` jest zwalniana i [CAutoPtr::m_p](#m_p) zmiennej składowej danych jest ustawiona na wartość NULL.  
  
##  <a name="m_p"></a>  CAutoPtr::m_p  
 Zmiennej składowej danych wskaźnika.  
  
```
T* m_p;
```  
  
### <a name="remarks"></a>Uwagi  
 Ta zmienna członka przechowuje informacje o wskaźnikach.  
  
##  <a name="operator_eq"></a>  CAutoPtr::operator =  
 Operator przypisania.  
  
```
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```  
  
### <a name="parameters"></a>Parametry  
 *p*  
 Wskaźnik.  
  
 *TSrc*  
 Typ klasy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do **CAutoPtr\< T >**.  
  
### <a name="remarks"></a>Uwagi  
 Operator przypisania odłącza `CAutoPtr` obiekt z dowolny wskaźnik bieżącego i dołącza nowy wskaźnik *p*, w tym miejscu.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład w [Przegląd CAutoPtr](../../atl/reference/cautoptr-class.md).  
  
##  <a name="operator_ptr"></a>  CAutoPtr::operator-&gt;  
 Operator wskaźnika do elementu członkowskiego.  
  
```
T* operator->() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość [CAutoPtr::m_p](#m_p) zmiennej składowej danych.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego operatora do wywołania metody w klasie, do których prowadzą `CAutoPtr` obiektu. W kompilacjach do debugowania błędu potwierdzenia wystąpi `CAutoPtr` wskazuje na wartość NULL.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład w [Przegląd CAutoPtr](../../atl/reference/cautoptr-class.md).  
  
##  <a name="operator_t_star"></a>  CAutoPtr::operator T *  
 Operator rzutowania.  
  
```  
operator T* () const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do typu danych obiektu zdefiniowane w szablonie klasy.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład w [Przegląd CAutoPtr](../../atl/reference/cautoptr-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CHeapPtr](../../atl/reference/cheapptr-class.md)   
 [Klasa CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
