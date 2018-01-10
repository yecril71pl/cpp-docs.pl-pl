---
title: Klasa CComDynamicUnkArray | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::Add
- ATLCOM/ATL::CComDynamicUnkArray::begin
- ATLCOM/ATL::CComDynamicUnkArray::clear
- ATLCOM/ATL::CComDynamicUnkArray::end
- ATLCOM/ATL::CComDynamicUnkArray::GetAt
- ATLCOM/ATL::CComDynamicUnkArray::GetCookie
- ATLCOM/ATL::CComDynamicUnkArray::GetSize
- ATLCOM/ATL::CComDynamicUnkArray::GetUnknown
- ATLCOM/ATL::CComDynamicUnkArray::Remove
dev_langs: C++
helpviewer_keywords:
- connection points [C++], managing
- CComDynamicUnkArray class
ms.assetid: 202470d7-9a1b-498f-b96d-659d681acd65
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5863c224ed47c70ce485bde3cd693c29afbfbc04
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ccomdynamicunkarray-class"></a>Klasa CComDynamicUnkArray
Ta klasa przechowuje tablicę **IUnknown** wskaźników.  
  
## <a name="syntax"></a>Składnia  
  
```
class CComDynamicUnkArray
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComDynamicUnkArray::CComDynamicUnkArray](#ccomdynamicunkarray)|Konstruktor. Inicjuje wartości kolekcji do **NULL** i rozmiaru kolekcji od zera.|  
|[CComDynamicUnkArray:: ~ CComDynamicUnkArray](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComDynamicUnkArray::Add](#add)|Wywołanie tej metody, aby dodać `IUnknown` wskaźnika do tablicy.|  
|[CComDynamicUnkArray::begin](#begin)|Zwraca wskaźnik do pierwszego `IUnknown` wskaźnika w kolekcji.|  
|[CComDynamicUnkArray::clear](#clear)|Opróżnia tablicy.|  
|[CComDynamicUnkArray::end](#end)|Zwraca wskaźnik do jednego poza ostatniego **IUnknown** wskaźnika w kolekcji.|  
|[CComDynamicUnkArray::GetAt](#getat)|Pobiera element pod określonym indeksem.|  
|[CComDynamicUnkArray::GetCookie](#getcookie)|Wywołanie tej metody, aby uzyskać plik cookie skojarzone z danym **IUnknown** wskaźnika.|  
|[CComDynamicUnkArray::GetSize](#getsize)|Zwraca długość tablicy.|  
|[CComDynamicUnkArray::GetUnknown](#getunknown)|Wywołanie tej metody, aby uzyskać **IUnknown** wskaźnika skojarzone z danym pliku cookie.|  
|[CComDynamicUnkArray::Remove](#remove)|Wywołanie tej metody, aby usunąć **IUnknown** wskaźnika z tablicy.|  
  
## <a name="remarks"></a>Uwagi  
 **CComDynamicUnkArray** przechowuje dynamicznie przydzielonego tablicę **IUnknown** wskaźniki, każdy punkt interfejsu połączenia. **CComDynamicUnkArray** mogą być używane jako parametr [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) klasy szablonu.  
  
 **CComDynamicUnkArray** metody [rozpocząć](#begin) i [zakończenia](#end) może służyć do pętli wszystkie punkty połączenia (na przykład, gdy zdarzenie jest wywoływane).  
  
 Zobacz [dodanie do niej punkty połączenia do obiektu](../../atl/adding-connection-points-to-an-object.md) szczegółowe informacje na temat automatyzacji tworzenia połączenia punktu proxy.  
  
> [!NOTE]
> **Uwaga** klasy **CComDynamicUnkArray** jest używany przez **Dodaj klasę** kreatora podczas tworzenia formant, który ma punkty połączenia. Jeśli chcesz ręcznie określić liczbę punktów połączenia, zmień odwołania z **CComDynamicUnkArray** do `CComUnkArray<`  *n*  `>`, gdzie  *n*  jest liczba punktów połączenia wymagane.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="add"></a>CComDynamicUnkArray::Add  
 Wywołanie tej metody, aby dodać **IUnknown** wskaźnika do tablicy.  
  
```
DWORD Add(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnk*  
 **IUnknown** wskaźnika, aby dodać do tablicy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca plik cookie skojarzone z nowo dodanego wskaźnika.  
  
##  <a name="begin"></a>CComDynamicUnkArray::begin  
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
  
##  <a name="clear"></a>CComDynamicUnkArray::clear  
 Opróżnia tablicy.  
  
```
void clear();
```  
  
##  <a name="ccomdynamicunkarray"></a>CComDynamicUnkArray::CComDynamicUnkArray  
 Konstruktor.  
  
```
CComDynamicUnkArray();
```  
  
### <a name="remarks"></a>Uwagi  
 Ustawia rozmiar kolekcji od zera i inicjuje wartości do **NULL**. Destruktor zwalnia kolekcji, jeśli to konieczne.  
  
##  <a name="dtor"></a>CComDynamicUnkArray:: ~ CComDynamicUnkArray  
 Destruktor.  
  
```
~CComDynamicUnkArray();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia zasoby przydzielone przez konstruktora klasy.  
  
##  <a name="end"></a>CComDynamicUnkArray::end  
 Zwraca wskaźnik do jednego poza ostatniego **IUnknown** wskaźnika w kolekcji.  
  
```
IUnknown**
    end();
```     
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do **IUnknown** wskaźnika interfejsu.  
  
##  <a name="getat"></a>CComDynamicUnkArray::GetAt  
 Pobiera element pod określonym indeksem.  
  
```
IUnknown* GetAt(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks elementu do pobrania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) interfejsu.  
  
##  <a name="getcookie"></a>CComDynamicUnkArray::GetCookie  
 Wywołanie tej metody, aby uzyskać plik cookie skojarzone z danym **IUnknown** wskaźnika.  
  
```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```  
  
### <a name="parameters"></a>Parametry  
 `ppFind`  
 **IUnknown** wskaźnika, dla których skojarzony plik cookie jest wymagana.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca plik cookie skojarzone z **IUnknown** wskaźnika lub zero, jeśli pasujących **IUnknown** znajduje się wskaźnik.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli istnieje więcej niż jedno wystąpienie tego samego **IUnknown** wskaźnika, ta funkcja zwraca wartość pliku cookie dla pierwszego z nich.  
  
##  <a name="getsize"></a>CComDynamicUnkArray::GetSize  
 Zwraca długość tablicy.  
  
```
int GetSize() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Długość tablicy.  
  
##  <a name="getunknown"></a>CComDynamicUnkArray::GetUnknown  
 Wywołanie tej metody, aby uzyskać **IUnknown** wskaźnika skojarzone z danym pliku cookie.  
  
```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```  
  
### <a name="parameters"></a>Parametry  
 `dwCookie`  
 Plik cookie, dla których skojarzone **IUnknown** wskaźnika jest wymagana.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **IUnknown** wskaźnika lub wartość NULL, jeśli nie dopasowania zostanie znaleziony cookie.  
  
##  <a name="remove"></a>CComDynamicUnkArray::Remove  
 Wywołanie tej metody, aby usunąć **IUnknown** wskaźnika z tablicy.  
  
```
BOOL Remove(DWORD dwCookie);
```  
  
### <a name="parameters"></a>Parametry  
 `dwCookie`  
 Odwołanie do pliku cookie **IUnknown** wskaźnika do usunięcia z tablicy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli wskaźnik jest usunięte; w przeciwnym razie wartość FALSE.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComUnkArray](../../atl/reference/ccomunkarray-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
