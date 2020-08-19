---
title: wbuffer_convert — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocmon/stdext::cvt::wbuffer_convert
helpviewer_keywords:
- wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
ms.openlocfilehash: ba8c98075741ae6cb8db0ecdfcb1e18cf4f4f89c
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561118"
---
# <a name="wbuffer_convert-class"></a>wbuffer_convert — Klasa

Opisuje bufor strumienia, który kontroluje przekazywanie elementów do i z bufora strumienia bajtów.

## <a name="syntax"></a>Składnia

```cpp
template <class Codecvt, class Elem = wchar_t, class Traits = std::char_traits<Elem>>
class wbuffer_convert
    : public std::basic_streambuf<Elem, Traits>
```

### <a name="parameters"></a>Parametry

*Codecvt*\
Zestaw reguł [ustawień regionalnych](../standard-library/locale-class.md) , który reprezentuje obiekt konwersji.

*Elem*\
Typ elementu dwubajtowego.

*Cech*\
Cechy skojarzone z *elem*.

## <a name="remarks"></a>Uwagi

Ten szablon klasy opisuje bufor strumienia, który kontroluje przekazywanie elementów typu `_Elem` , których cechy znakowe są opisane przez klasę `Traits` , do i z bufora strumienia bajtów typu `std::streambuf` .

Konwersja między sekwencją `Elem` wartości i sekwencją wielobajtową jest wykonywana przez obiekt klasy `Codecvt<Elem, char, std::mbstate_t>` , który spełnia wymagania standardowego aspektu konwersji kodu `std::codecvt<Elem, char, std::mbstate_t>` .

Obiekt tego szablonu klasy przechowuje:

- Wskaźnik do buforu strumienia bajtów źródłowych

- Wskaźnik do przydzielony obiekt konwersji (zwolniony, gdy [wbuffer_convert](../standard-library/wbuffer-convert-class.md)
