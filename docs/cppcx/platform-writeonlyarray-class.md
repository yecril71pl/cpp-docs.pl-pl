---
title: Platform::WriteOnlyArray, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::WriteOnlyArray::begin
- VCCORLIB/Platform::WriteOnlyArray::Data
- VCCORLIB/Platform::WriteOnlyArray::end
- VCCORLIB/Platform::WriteOnlyArray::FastPass
- VCCORLIB/Platform::WriteOnlyArray::Length
- VCCORLIB/Platform::WriteOnlyArray::set
dev_langs:
- C++
helpviewer_keywords:
- Platform::WriteOnlyArray Class
ms.assetid: 92d7dd56-ec58-4b8c-88ba-9c903668b687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3871b6ad3aead88c32c906726f689d949eb945ba
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603349"
---
# <a name="platformwriteonlyarray-class"></a>Platform::WriteOnlyArray, klasa
Reprezentuje Jednowymiarowa tablica, która jest używana jako parametr wejściowy, gdy wywołanie metody do wypełnienia tablicy.  
  
 Ta klasa ref jest zadeklarowany jako prywatny w vccorlib.h; dlatego nie jest emitowane w metadanych i jest tylko może być używany przez C++. Ta klasa jest przeznaczona tylko do użytku jako parametr wejściowy, który odbiera tablicę, która została przydzielona przez obiekt wywołujący. Nie jest konstrukcyjną z kodu użytkownika. Umożliwia ona metody C++ do zapisu bezpośrednio do tablicy — wzorzec, który jest znany jako *FillArray* wzorca. Aby uzyskać więcej informacji, zobacz [tablica i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
private ref class WriteOnlyArray<T, 1>  
```  
  
### <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
 Te metody mają wewnętrznej dostępności — oznacza to, że tylko są one dostępne w języku C++ aplikacji lub składnika.  
  
|Nazwa|Opis|  
|----------|-----------------|  

|[WriteOnlyArray::begin](#begin)| Iterator, który wskazuje na pierwszy element tablicy. |  
|[WriteOnlyArray::Data](#data)| Wskaźnik do buforu danych. |  
|[WriteOnlyArray::end](#end)| Iterator, który wskazuje na po ostatnim elemencie w tablicy. |  
|[WriteOnlyArray::FastPass](#fastpass)| Wskazuje, czy tablica mogą używać mechanizmu FastPass, czyli optymalizacji, w sposób niewidoczny dla użytkownika wykonywane przez system. Nie używaj to w kodzie |  
|[WriteOnlyArray::Length](#length)| Zwraca liczbę elementów w tablicy. |  
|[WriteOnlyArray::set](#set)| Ustawia określony element z podaną wartością. |  

  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `WriteOnlyArray`  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
 **Metadane:** Platform.winmd  
  
 **Namespace:** platformy  

## <a name="begin"></a>  Metoda WriteOnlyArray::begin
Zwraca wskaźnik do pierwszego elementu w tablicy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
T* begin() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do pierwszego elementu w tablicy.  
  
### <a name="remarks"></a>Uwagi  
 Ta iteratora mogą być używane z algorytmami STL takich jak `std::sort` działanie w przypadku elementów w tablicy.  
  


## <a name="data"></a>  Właściwość WriteOnlyArray::Data
Wskaźnik do buforu danych.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
property T* Data{  
   T* get() const;  
}  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do pierwotnych tablicy bajtów.  
  


## <a name="end"></a>  Metoda WriteOnlyArray::end
Zwraca wskaźnik do pierwszego do ostatniego elementu w tablicy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
T* end() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator wskaźnik do pierwszego do ostatniego elementu w tablicy.  
  
### <a name="remarks"></a>Uwagi  
 Ta iteratora można za pomocą algorytmów STL wykonywać operacje, takie jak `std::sort` elementów tablicy.  
  


## <a name="fastpass"></a>  Właściwość WriteOnlyArray::FastPass
Wskazuje, czy wewnętrzny optymalizacji FastPass mogą być wykonywane. Nie przeznaczona do użytku przez kod użytkownika.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
property bool FastPass{  
   bool get() const;  
}  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość logiczna wskazująca, czy tablica dotyczy FastPass.  
  


## <a name="get"></a>  Metoda WriteOnlyArray::get
Zwraca element pod określonym indeksem.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
T& get(  
   unsigned int indexArg) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `indexArg`  
  
### <a name="return-value"></a>Wartość zwracana  
  


## <a name="length"></a>  Właściwość WriteOnlyArray::Length
Zwraca liczbę elementów w tablicy przydzielonej przez obiekt wywołujący.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
property unsigned int Length{  
   unsigned int get() const;  
}  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w tablicy.  
  


## <a name="set"></a>  WriteOnlyArray::set — funkcja
Ustawia określoną wartość w określonym indeksie w tablicy.  
  
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
 Aby uzyskać więcej informacji dotyczących sposobu interpretowania wartości HRESULT, zobacz [struktury COM kody błędów](http://go.microsoft.com/fwlink/p/?LinkId=262045).  
  
  
## <a name="see-also"></a>Zobacz też  
 [Namespace platformy](platform-namespace-c-cx.md)   
 [Tworzenie składników środowiska wykonawczego Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)