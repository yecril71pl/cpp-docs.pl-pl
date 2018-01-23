---
title: Klasa platform::WriteOnlyArray | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
s.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VCCORLIB/Platform::WriteOnlyArray::begin
- VCCORLIB/Platform::WriteOnlyArray::Data
- VCCORLIB/Platform::WriteOnlyArray::end
- VCCORLIB/Platform::WriteOnlyArray::FastPass
- VCCORLIB/Platform::WriteOnlyArray::Length
- VCCORLIB/Platform::WriteOnlyArray::set
dev_langs: C++
helpviewer_keywords: Platform::WriteOnlyArray Class
ms.assetid: 92d7dd56-ec58-4b8c-88ba-9c903668b687
caps.latest.revision: "11"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d63072e3190929f5191f3d515b73dbd6a6a75040
ms.sourcegitcommit: 6f40bba1772a09ff0e3843d5f70b553e1a15ab50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2018
---
# <a name="platformwriteonlyarray-class"></a>Klasa platform::WriteOnlyArray
Reprezentuje Jednowymiarowa tablica, która jest używana jako parametr wejściowy, gdy obiekt wywołujący tablicy dla metody do wypełnienia.  
  
 Ta klasa ref jest zadeklarowany jako prywatny w vccorlib.h; w związku z tym nie jest emitowany w metadanych i jest tylko eksploatacyjny z C++. Ta klasa jest przeznaczony tylko do użytku jako parametr wejściowy, który odbiera tablicy przydzielonej przez obiekt wywołujący. To nie umożliwia konstrukcji z kodu użytkownika. Umożliwia korzystanie z metody C++ do zapisania bezpośrednio w tablicy — wzorzec, który jest nazywany *FillArray* wzorca. Aby uzyskać więcej informacji, zobacz [tablicy i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
private ref class WriteOnlyArray<T, 1>  
```  
  
### <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
 Te metody mają wnętrza — to znaczy tylko są one dostępne w języku C++ aplikacji lub składnika.  
  
|Nazwa|Opis|  
|----------|-----------------|  

|[WriteOnlyArray::begin](#begin)| Iteratora wskazujące pierwszy element macierzy. |  
|[WriteOnlyArray::Data](#data)| Wskaźnik do buforu danych. |  
|[WriteOnlyArray::end](#end)| Iterator, który wskazuje po ostatnim elemencie tablicy. |  
|[WriteOnlyArray::FastPass](#fastpass)| Wskazuje, czy tablicy mogą używać mechanizmu FastPass to Optymalizacja niewidocznie wykonywanych przez system. Nie używaj to w kodzie |  
|[WriteOnlyArray::Length](#length)| Zwraca liczbę elementów w tablicy. |  
|[WriteOnlyArray::set](#set)| Ustawia określony element z podaną wartością. |  

  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `WriteOnlyArray`  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
 **Metadane:** Platform.winmd  
  
 **Namespace:** platformy  

## <a name="begin"></a>WriteOnlyArray::begin — metoda
Zwraca wskaźnik do pierwszego elementu w tablicy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
T* begin() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do pierwszego elementu w tablicy.  
  
### <a name="remarks"></a>Uwagi  
 Iterator ten może być używany z algorytmów STL takich jak `std::sort` do działania na elementów w tablicy.  
  


## <a name="data"></a>Właściwość WriteOnlyArray::Data
Wskaźnik do buforu danych.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
property T* Data{  
   T* get() const;  
}  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nieprzetworzonej tablicy bajtów.  
  


## <a name="end"></a>WriteOnlyArray::end — metoda
Zwraca wskaźnik do jednego po ostatnim elemencie tablicy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
T* end() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator wskaźnika do jednego po ostatnim elemencie tablicy.  
  
### <a name="remarks"></a>Uwagi  
 Ta iteratora może służyć STL algorytmów w celu wykonania operacji, takich jak `std::sort` dla elementów tablicy.  
  


## <a name="fastpass"></a>Właściwość WriteOnlyArray::FastPass
Wskazuje, czy należy przeprowadzić wewnętrzny optymalizacji FastPass. Nie przeznaczone do użytku przez kod użytkownika.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
property bool FastPass{  
   bool get() const;  
}  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość logiczna wskazująca, czy tablica jest FastPass.  
  


## <a name="get"></a>WriteOnlyArray::get — metoda
Zwraca element pod określonym indeksem.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
T& get(  
   unsigned int indexArg) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `indexArg`  
  
### <a name="return-value"></a>Wartość zwracana  
  


## <a name="length"></a>Właściwość WriteOnlyArray::Length
Zwraca liczbę elementów w tablicy przydzielone przez obiekt wywołujący.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
property unsigned int Length{  
   unsigned int get() const;  
}  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w tablicy.  
  


## <a name="set"></a>Funkcja WriteOnlyArray::set
Ustawia określoną wartość od określonego indeksu tablicy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
T& set(  
   unsigned int indexArg,  
   T valueArg);  
```  
  
### <a name="parameters"></a>Parametry  
 `indexArg`  
 Indeks elementu do ustawienia.  
  
 `valueArg`  
 Wartość do ustawienia w `indexArg`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do elementu, który właśnie został ustawiony.  
  

  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji dotyczących sposobu interpretowania wartość HRESULT, zobacz [struktury COM kody błędów](http://go.microsoft.com/fwlink/p/?LinkId=262045).  
  
  
## <a name="see-also"></a>Zobacz też  
 [Namespace platformy](platform-namespace-c-cx.md)   
 [Tworzenie składników środowiska wykonawczego systemu Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)