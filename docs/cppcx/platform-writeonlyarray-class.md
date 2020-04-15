---
title: Platform::WriteOnlyArray, klasa
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::WriteOnlyArray::begin
- VCCORLIB/Platform::WriteOnlyArray::Data
- VCCORLIB/Platform::WriteOnlyArray::end
- VCCORLIB/Platform::WriteOnlyArray::FastPass
- VCCORLIB/Platform::WriteOnlyArray::Length
- VCCORLIB/Platform::WriteOnlyArray::set
helpviewer_keywords:
- Platform::WriteOnlyArray Class
ms.assetid: 92d7dd56-ec58-4b8c-88ba-9c903668b687
ms.openlocfilehash: d06ed19b7c041f9ae73f862ba521449a206aa321
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374644"
---
# <a name="platformwriteonlyarray-class"></a>Platform::WriteOnlyArray, klasa

Reprezentuje tablicę jednowymiarową, która jest używana jako parametr wejściowy, gdy wywołujący przekazuje tablicę dla metody do wypełnienia.

Ta klasa ref jest zadeklarowana jako prywatna w vccorlib.h; w związku z tym nie jest emitowany w metadanych i jest tylko materiały eksploatacyjne z języka C++. Ta klasa jest przeznaczona tylko do użycia jako parametr wejściowy, który odbiera tablicę, która została przydzielona przez obiekt wywołujący. Nie jest konstruowany z kodu użytkownika. Umożliwia metodę C++ do zapisu bezpośrednio do tej tablicy — wzorzec, który jest znany jako *FillArray* wzorca. Aby uzyskać więcej informacji, zobacz [Tablica i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="syntax"></a>Składnia

```cpp
private ref class WriteOnlyArray<T, 1>
```

### <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

Te metody mają dostęp wewnętrzny — oznacza to, że są one dostępne tylko w aplikacji lub składniku C++.

|Nazwa|Opis|
|----------|-----------------|
|[WriteOnlyArray::begin](#begin)|Iterator, który wskazuje na pierwszy element tablicy.|
|[WriteOnlyArray::Data](#data)|Wskaźnik do buforu danych.|
|[WriteOnlyArray::end](#end)|Iterator, który wskazuje jeden przeszłości ostatni element w tablicy.|
|[WriteOnlyArray::FastPass](#fastpass)|Wskazuje, czy tablica może korzystać z mechanizmu FastPass, który jest optymalizacją w sposób przezroczysty wykonywany przez system. Nie używaj tego w kodzie|
|[WriteOnlyArray::Długość](#length)|Zwraca liczbę elementów w tablicy.|
|[WriteOnlyArray::set](#set)|Ustawia określony element na określoną wartość.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`WriteOnlyArray`

### <a name="requirements"></a>Wymagania

Opcja kompilatora: **/ZW**

**Metadane:** Platforma.winmd

**Obszar nazw:** Platformy

## <a name="writeonlyarraybegin-method"></a><a name="begin"></a>WriteOnlyArray::begin Metoda

Zwraca wskaźnik do pierwszego elementu w tablicy.

### <a name="syntax"></a>Składnia

```cpp
T* begin() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego elementu w tablicy.

### <a name="remarks"></a>Uwagi

Ten iterator może służyć z algorytmami `std::sort` STL, takich jak do pracy na elementach w tablicy.

## <a name="writeonlyarraydata-property"></a><a name="data"></a>WriteOnlyArray::Data Właściwość

Wskaźnik do buforu danych.

### <a name="syntax"></a>Składnia

```cpp
property T* Data{
   T* get() const;
}
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nieprzetworzonych bajtów tablicy.

## <a name="writeonlyarrayend-method"></a><a name="end"></a>WriteOnlyArray::end Metoda

Zwraca wskaźnik do jednego przeszłości ostatni element w tablicy.

### <a name="syntax"></a>Składnia

```cpp
T* end() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator wskaźnika do jednego przeszłości ostatni element w tablicy.

### <a name="remarks"></a>Uwagi

Ten iterator może służyć z algorytmami STL `std::sort` do wykonywania operacji, takich jak na elementy tablicy.

## <a name="writeonlyarrayfastpass-property"></a><a name="fastpass"></a>WriteOnlyArray::Właściwość FastPass

Wskazuje, czy można wykonać wewnętrzną optymalizację FastPass. Nie jest przeznaczony do użycia przez kod użytkownika.

### <a name="syntax"></a>Składnia

```cpp
property bool FastPass{
   bool get() const;
}
```

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna wskazująca, czy tablica jest FastPass.

## <a name="writeonlyarrayget-method"></a><a name="get"></a>WriteOnlyArray::get Metoda

Zwraca element w określonym indeksie.

### <a name="syntax"></a>Składnia

```cpp
T& get(unsigned int indexArg) const;
```

### <a name="parameters"></a>Parametry

*indeksArg*<br/>
Indeks do użycia.

### <a name="return-value"></a>Wartość zwracana

## <a name="writeonlyarraylength-property"></a><a name="length"></a>WriteOnlyArray::Właściwość Length

Zwraca liczbę elementów w tablicy przydzielonej przez wywołującego.

### <a name="syntax"></a>Składnia

```cpp
property unsigned int Length{
   unsigned int get() const;
}
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w tablicy.

## <a name="writeonlyarrayset-function"></a><a name="set"></a>WriteOnlyArray::set Funkcja

Ustawia określoną wartość w określonym indeksie w tablicy.

### <a name="syntax"></a>Składnia

```cpp
T& set(
   unsigned int indexArg,
   T valueArg);
```

### <a name="parameters"></a>Parametry

*indeksArg*<br/>
Indeks elementu do ustawionego.

*wartośćArg*<br/>
Wartość ustawiona `indexArg`na .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu, który został właśnie ustawiony.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat interpretowania wartości HRESULT, zobacz [Struktura kodów błędów COM](/windows/win32/com/structure-of-com-error-codes).

## <a name="see-also"></a>Zobacz też

[Obszar nazw platformy](platform-namespace-c-cx.md)<br/>
[Tworzenie składników środowiska wykonawczego systemu Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
