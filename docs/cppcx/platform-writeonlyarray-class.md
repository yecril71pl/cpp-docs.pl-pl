---
title: 'Platform:: WriteOnlyArray, Klasa'
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
ms.openlocfilehash: 5652123d4866262515f804dba790af51610eb426
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500522"
---
# <a name="platformwriteonlyarray-class"></a>Platform:: WriteOnlyArray, Klasa

Reprezentuje tablicę jednowymiarową używaną jako parametr wejściowy, gdy obiekt wywołujący przekazuje tablicę dla metody do wypełnienia.

Ta klasa referencyjna jest zadeklarowana jako prywatna w vccorlib. h; w związku z tym nie jest emitowany w metadanych i można go używać tylko C++z. Ta klasa jest przeznaczona tylko do użycia jako parametr wejściowy, który odbiera tablicę przydzieloną przez wywołującego. Nie jest konstrukcyjną od kodu użytkownika. Umożliwia C++ metodę zapisu bezpośrednio w tej tablicy — wzorzec, który jest znany jako wzorzec *metodzie FillArray* . Aby uzyskać więcej informacji, zobacz [Array i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="syntax"></a>Składnia

```cpp
private ref class WriteOnlyArray<T, 1>
```

### <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

Te metody mają wewnętrzny dostęp — to znaczy, że są dostępne tylko w ramach C++ aplikacji lub składnika.

|Nazwa|Opis|
|----------|-----------------|
|[WriteOnlyArray:: BEGIN](#begin)|Iterator, który wskazuje na pierwszy element tablicy.|
|[WriteOnlyArray::D ATA](#data)|Wskaźnik do buforu danych.|
|[WriteOnlyArray:: end](#end)|Iterator, który wskazuje jeden poza ostatnim elementem w tablicy.|
|[WriteOnlyArray:: FastPass](#fastpass)|Wskazuje, czy tablica może korzystać z mechanizmu FastPass, który jest optymalizacją niewidocznie wykonywaną przez system. Nie używaj tego w kodzie|
|[WriteOnlyArray:: length](#length)|Zwraca liczbę elementów w tablicy.|
|[WriteOnlyArray:: Set](#set)|Ustawia określony element na określoną wartość.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`WriteOnlyArray`

### <a name="requirements"></a>Wymagania

Opcja kompilatora: **/zw**

**Metadane** Obiekt platform. winmd

**Obszaru** Platforma

## <a name="begin"></a>WriteOnlyArray:: BEGIN — Metoda

Zwraca wskaźnik do pierwszego elementu w tablicy.

### <a name="syntax"></a>Składnia

```cpp
T* begin() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego elementu w tablicy.

### <a name="remarks"></a>Uwagi

Ten iterator może być używany z algorytmami STL, `std::sort` takimi jak wykonywanie operacji na elementach tablicy.

## <a name="data"></a>WriteOnlyArray::D ATA — Właściwość

Wskaźnik do buforu danych.

### <a name="syntax"></a>Składnia

```cpp
property T* Data{
   T* get() const;
}
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nieprzetworzonych bajtów tablicowych.

## <a name="end"></a>WriteOnlyArray:: end — Metoda

Zwraca wskaźnik do jednego z ostatnich elementów w tablicy.

### <a name="syntax"></a>Składnia

```cpp
T* end() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator wskaźnika do jednego z ostatnich elementów w tablicy.

### <a name="remarks"></a>Uwagi

Ten iterator może być używany z algorytmami STL do wykonywania operacji, `std::sort` takich jak w przypadku elementów tablicy.

## <a name="fastpass"></a>WriteOnlyArray:: FastPass, właściwość

Wskazuje, czy można wykonać wewnętrzną optymalizację FastPass. Nie przeznaczony do użycia przez kod użytkownika.

### <a name="syntax"></a>Składnia

```cpp
property bool FastPass{
   bool get() const;
}
```

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna wskazująca, czy tablica jest FastPass.

## <a name="get"></a>WriteOnlyArray:: Get — Metoda

Zwraca element o określonym indeksie.

### <a name="syntax"></a>Składnia

```cpp
T& get(unsigned int indexArg) const;
```

### <a name="parameters"></a>Parametry

*indexArg*<br/>
Indeks do użycia.

### <a name="return-value"></a>Wartość zwracana

## <a name="length"></a>WriteOnlyArray:: Length — właściwość

Zwraca liczbę elementów w tablicy przydzielonym przez obiekt wywołujący.

### <a name="syntax"></a>Składnia

```cpp
property unsigned int Length{
   unsigned int get() const;
}
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w tablicy.

## <a name="set"></a>WriteOnlyArray:: Set — funkcja

Ustawia określoną wartość w określonym indeksie w tablicy.

### <a name="syntax"></a>Składnia

```cpp
T& set(
   unsigned int indexArg,
   T valueArg);
```

### <a name="parameters"></a>Parametry

*indexArg*<br/>
Indeks elementu, który ma zostać ustawiony.

*valueArg*<br/>
Wartość, która ma zostać `indexArg`ustawiona na.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu, który został właśnie ustawiony.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat interpretowania wartości HRESULT, zobacz [struktury kodów błędów modelu COM](/windows/win32/com/structure-of-com-error-codes).

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](platform-namespace-c-cx.md)<br/>
[Tworzenie składników środowisko wykonawcze systemu Windows w programieC++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
