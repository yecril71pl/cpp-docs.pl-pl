---
title: Klasa CComUnkArray | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComUnkArray
- ATLCOM/ATL::CComUnkArray
- ATLCOM/ATL::CComUnkArray::CComUnkArray
- ATLCOM/ATL::CComUnkArray::Add
- ATLCOM/ATL::CComUnkArray::begin
- ATLCOM/ATL::CComUnkArray::end
- ATLCOM/ATL::CComUnkArray::GetCookie
- ATLCOM/ATL::CComUnkArray::GetUnknown
- ATLCOM/ATL::CComUnkArray::Remove
dev_langs: C++
helpviewer_keywords:
- connection points [C++], managing
- CComUnkArray class
ms.assetid: 5fd4b378-a7b5-4cc1-8866-8ab72a73639e
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 14c2b7e05ed303d8b18ae40619bc63a75f025662
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccomunkarray-class"></a>Klasa CComUnkArray
Ta klasa przechowuje **IUnknown** wskaźniki i jest przeznaczony do użycia jako parametr [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) klasy szablonu.  
  
## <a name="syntax"></a>Składnia  
  
```
template<unsigned int nMaxSize>
class CComUnkArray
```  
  
#### <a name="parameters"></a>Parametry  
 *nMaxSize*  
 Maksymalna liczba **IUnknown** wskaźników, które można przechowywać w statycznej tablicy.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComUnkArray::CComUnkArray](#ccomunkarray)|Konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComUnkArray::Add](#add)|Wywołanie tej metody, aby dodać **IUnknown** wskaźnika do tablicy.|  
|[CComUnkArray::begin](#begin)|Zwraca wskaźnik do pierwszego **IUnknown** wskaźnika w kolekcji.|  
|[CComUnkArray::end](#end)|Zwraca wskaźnik do jednego poza ostatniego **IUnknown** wskaźnika w kolekcji.|  
|[CComUnkArray::GetCookie](#getcookie)|Wywołanie tej metody, aby uzyskać plik cookie skojarzone z danym **IUnknown** wskaźnika.|  
|[CComUnkArray::GetUnknown](#getunknown)|Wywołanie tej metody, aby uzyskać **IUnknown** wskaźnika skojarzone z danym pliku cookie.|  
|[CComUnkArray::Remove](#remove)|Wywołanie tej metody, aby usunąć **IUnknown** wskaźnika z tablicy.|  
  
## <a name="remarks"></a>Uwagi  
 **CComUnkArray** przechowuje stałej liczby **IUnknown** wskaźniki, każdy punkt interfejsu połączenia. **CComUnkArray** mogą być używane jako parametr [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) klasy szablonu. **CComUnkArray\<1 >** jest specjalizacją szablonu **CComUnkArray** który został zoptymalizowany dla punktu jedno połączenie.  
  
 **CComUnkArray** metody [rozpocząć](#begin) i [zakończenia](#end) może służyć do pętli wszystkie punkty połączenia (na przykład, gdy zdarzenie jest wywoływane).  
  
 Zobacz [dodanie do niej punkty połączenia do obiektu](../../atl/adding-connection-points-to-an-object.md) szczegółowe informacje na temat automatyzacji tworzenia połączenia punktu proxy.  
  
> [!NOTE]
> **Uwaga** klasy [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md) jest używany przez **Dodaj klasę** kreatora podczas tworzenia formant, który ma punkty połączenia. Jeśli chcesz ręcznie określić liczbę punktów połączenia, zmień odwołania z **CComDynamicUnkArray** do `CComUnkArray<`  *n*  `>`, gdzie  *n*  jest liczba punktów połączenia wymagane.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="add"></a>CComUnkArray::Add  
 Wywołanie tej metody, aby dodać **IUnknown** wskaźnika do tablicy.  
  
```
DWORD Add(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnk*  
 Wywołanie tej metody, aby dodać **IUnknown** wskaźnika do tablicy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca plik cookie skojarzone z nowo dodanego wskaźnika lub 0, jeśli tablica nie jest wystarczająco duży, aby zawierać nowego wskaźnika.  
  
##  <a name="begin"></a>CComUnkArray::begin  
 Zwraca kursor na początku kolekcji **IUnknown** wskaźniki interfejsu.  
  
```
IUnknown**
    begin();
```     
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do **IUnknown** wskaźnika interfejsu.  
  
### <a name="remarks"></a>Uwagi  
 Kolekcja zawiera wskaźniki do interfejsów lokalnie przechowywane jako **IUnknown**. Rzutowanie każdego **IUnknown** interfejsu do typu rzeczywistego interfejs, a następnie wywołać przy jego użyciu. Nie trzeba najpierw zapytania dla interfejsu.  
  
 Przed użyciem **IUnknown** interfejsu, należy sprawdzić, czy nie jest **NULL**.  
  
##  <a name="ccomunkarray"></a>CComUnkArray::CComUnkArray  
 Konstruktor.  
  
```
CComUnkArray();
```  
  
### <a name="remarks"></a>Uwagi  
 Ustawia kolekcję do przechowywania `nMaxSize` **IUnknown** wskaźniki i inicjuje wskaźniki do **NULL**.  
  
##  <a name="end"></a>CComUnkArray::end  
 Zwraca wskaźnik do jednego poza ostatniego **IUnknown** wskaźnika w kolekcji.  
  
```
IUnknown**
    end();
```     
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do **IUnknown** wskaźnika interfejsu.  
  
### <a name="remarks"></a>Uwagi  
 `CComUnkArray` Metody **rozpocząć** i **zakończenia** może służyć do pętli wszystkich punktów połączenia, na przykład, gdy zdarzenie jest wywoływane.  
  
 [!code-cpp[NVC_ATL_COM#44](../../atl/codesnippet/cpp/ccomunkarray-class_1.cpp)]  
  
##  <a name="getcookie"></a>CComUnkArray::GetCookie  
 Wywołanie tej metody, aby uzyskać plik cookie skojarzone z danym **IUnknown** wskaźnika.  
  
```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```  
  
### <a name="parameters"></a>Parametry  
 `ppFind`  
 **IUnknown** wskaźnika, dla których skojarzony plik cookie jest wymagana.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca plik cookie skojarzone z **IUnknown** wskaźnika lub 0, jeśli pasujących **IUnknown** znajduje się wskaźnik.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli istnieje więcej niż jedno wystąpienie tego samego **IUnknown** wskaźnika, ta funkcja zwraca wartość pliku cookie dla pierwszego z nich.  
  
##  <a name="getunknown"></a>CComUnkArray::GetUnknown  
 Wywołanie tej metody, aby uzyskać **IUnknown** wskaźnika skojarzone z danym pliku cookie.  
  
```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```  
  
### <a name="parameters"></a>Parametry  
 `dwCookie`  
 Plik cookie, dla których skojarzone **IUnknown** wskaźnika jest wymagana.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **IUnknown** wskaźnika lub wartość NULL, jeśli nie dopasowania zostanie znaleziony cookie.  
  
##  <a name="remove"></a>CComUnkArray::Remove  
 Wywołanie tej metody, aby usunąć **IUnknown** wskaźnika z tablicy.  
  
```
BOOL Remove(DWORD dwCookie);
```  
  
### <a name="parameters"></a>Parametry  
 `dwCookie`  
 Odwołanie do pliku cookie **IUnknown** wskaźnika do usunięcia z tablicy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** usunięcie wskaźnika **FALSE** inaczej.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
