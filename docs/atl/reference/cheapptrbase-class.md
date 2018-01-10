---
title: Klasa CHeapPtrBase | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase::AllocateBytes
- ATLCORE/ATL::CHeapPtrBase::Attach
- ATLCORE/ATL::CHeapPtrBase::Detach
- ATLCORE/ATL::CHeapPtrBase::Free
- ATLCORE/ATL::CHeapPtrBase::ReallocateBytes
- ATLCORE/ATL::CHeapPtrBase::m_pData
dev_langs: C++
helpviewer_keywords: CHeapPtrBase class
ms.assetid: 501ac1b2-fb34-4c72-b7e6-a4f1fc8fda21
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 59520211ae577c4ca4358874ef1d8ff71de59921
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cheapptrbase-class"></a>Klasa CHeapPtrBase
Ta klasa stanowi podstawę dla kilku klas wskaźnika inteligentnego stosu.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T, class Allocator = CCRTAllocator>  
class CHeapPtrBase
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ obiektu do zapisania na stosie.  
  
 `Allocator`  
 Klasa alokacji pamięci do użycia. Domyślnie CRT procedury służą do przydzielania i zwolnić pamięć.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHeapPtrBase:: ~ CHeapPtrBase](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHeapPtrBase::AllocateBytes](#allocatebytes)|Wywołanie tej metody można przydzielić pamięci.|  
|[CHeapPtrBase::Attach](#attach)|Wywołaj tę metodę, aby przejąć na własność istniejącego wskaźnika.|  
|[CHeapPtrBase::Detach](#detach)|Wywołanie tej metody, aby zwolnić własność wskaźnika.|  
|[CHeapPtrBase::Free](#free)|Wywołanie tej metody, aby usunąć obiekt wskazywany przez `CHeapPtrBase`.|  
|[CHeapPtrBase::ReallocateBytes](#reallocatebytes)|Wywołaj tę metodę, aby ponownie przydzielić pamięci.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHeapPtrBase::operator T *](#operator_t_star)|Operator rzutowania.|  
|[CHeapPtrBase::operator &](#operator_amp)|& — Operator.|  
|[CHeapPtrBase::operator ->](#operator_ptr)|Operator wskaźnika do elementu członkowskiego.|  

  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHeapPtrBase::m_pData](#m_pdata)|Zmienna elementu członkowskiego danych wskaźnika.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa stanowi podstawę dla kilku klas wskaźnika inteligentnego stosu. Klasy pochodne, na przykład [CHeapPtr](../../atl/reference/cheapptr-class.md) i [CComHeapPtr](../../atl/reference/ccomheapptr-class.md), dodaj ich konstruktory i operatory. Zobacz te klasy Przykłady implementacji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcore.h  
  
##  <a name="allocatebytes"></a>CHeapPtrBase::AllocateBytes  
 Wywołanie tej metody można przydzielić pamięci.  
  
```
bool AllocateBytes(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBytes`  
 Liczba bajtów pamięci do przydzielenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli pomyślnie jest pamięć przydzielona, wartość false w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli [CHeapPtrBase::m_pData](#m_pdata) zmiennej członkowskiej wskazuje obecnie istniejącej wartości; oznacza to, że nie jest równa NULL.  
  
##  <a name="attach"></a>CHeapPtrBase::Attach  
 Wywołaj tę metodę, aby przejąć na własność istniejącego wskaźnika.  
  
```
void Attach(T* pData) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pData`  
 `CHeapPtrBase` Obiektu będzie przejąć na własność ten wskaźnik.  
  
### <a name="remarks"></a>Uwagi  
 Gdy `CHeapPtrBase` obiektu przejmuje wskaźnik, automatycznie usunie wskaźnik i przydzielone dane podczas przechodzi ona poza zakresem.  
  
 W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli [CHeapPtrBase::m_pData](#m_pdata) zmiennej członkowskiej wskazuje obecnie istniejącej wartości; oznacza to, że nie jest równa NULL.  
  
##  <a name="dtor"></a>CHeapPtrBase:: ~ CHeapPtrBase  
 Destruktor.  
  
```
~CHeapPtrBase() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie przydzielone zasoby.  
  
##  <a name="detach"></a>CHeapPtrBase::Detach  
 Wywołanie tej metody, aby zwolnić własność wskaźnika.  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca kopię wskaźnika.  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia własność wskaźnik, ustawia [CHeapPtrBase::m_pData](#m_pdata) zmiennej członkowskiej na wartość NULL i zwraca kopię wskaźnika.  
  
##  <a name="free"></a>CHeapPtrBase::Free  
 Wywołanie tej metody, aby usunąć obiekt wskazywany przez `CHeapPtrBase`.  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Obiekt wskazywany przez `CHeapPtrBase` zostanie zwolniona i [CHeapPtrBase::m_pData](#m_pdata) zmiennej członkowskiej jest równa NULL.  
  
##  <a name="m_pdata"></a>CHeapPtrBase::m_pData  
 Zmienna elementu członkowskiego danych wskaźnika.  
  
```
T* m_pData;
```  
  
### <a name="remarks"></a>Uwagi  
 Ta zmienna elementu członkowskiego zawiera informacje wskaźnika.  
  
##  <a name="operator_amp"></a>CHeapPtrBase::operator&amp;  
 & — Operator.  
  
```
T** operator&() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca adres wskazywanego przez obiekt `CHeapPtrBase` obiektu.  
  

##  <a name="operator_ptr"></a>CHeapPtrBase::operator-&gt;  

 Operator wskaźnika do elementu członkowskiego.  
  
```
T* operator->() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość [CHeapPtrBase::m_pData](#m_pdata) zmiennej członkowskiej.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego operatora, aby wywołać metodę w klasie wskazywana przez `CHeapPtrBase` obiektu. W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli `CHeapPtrBase` wskazuje na wartość NULL.  
  
##  <a name="operator_t_star"></a>CHeapPtrBase::operator T *  
 Operator rzutowania.  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwraca [CHeapPtrBase::m_pData](#m_pdata).  
  
##  <a name="reallocatebytes"></a>CHeapPtrBase::ReallocateBytes  
 Wywołaj tę metodę, aby ponownie przydzielić pamięci.  
  
```
bool ReallocateBytes(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBytes`  
 Nowe ilość pamięci do przydzielenia w bajtach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli pomyślnie jest pamięć przydzielona, wartość false w przeciwnym razie wartość.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CHeapPtr](../../atl/reference/cheapptr-class.md)   
 [Klasa CComHeapPtr](../../atl/reference/ccomheapptr-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
