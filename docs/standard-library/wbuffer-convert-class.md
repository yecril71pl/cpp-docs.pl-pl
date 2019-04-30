---
title: wbuffer_convert — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocmon/stdext::cvt::wbuffer_convert
helpviewer_keywords:
- wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
ms.openlocfilehash: d19abf74bd9f794bc39ce04e5ed22e360cde75b4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410892"
---
# <a name="wbufferconvert-class"></a>wbuffer_convert — Klasa

W tym artykule opisano buforu strumieni, który kontroluje przekazywanie elementów do i z buforu strumienia bajtów.

## <a name="syntax"></a>Składnia

```cpp
template <class Codecvt, class Elem = wchar_t, class Traits = std::char_traits<Elem>>
class wbuffer_convert
    : public std::basic_streambuf<Elem, Traits>
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Codecvt*|[Ustawień regionalnych](../standard-library/locale-class.md) reguł, który reprezentuje obiekt konwersji.|
|*Elem*|Typ elementu znaków dwubajtowych.|
|*Cechy*|Cechy skojarzone z *Elem*.|

## <a name="remarks"></a>Uwagi

Ta klasa szablonu opisuje buforu strumieni, który kontroluje transmisji elementów typu `_Elem`, którego cech są opisane przez klasę `Traits`, do i z typu bufor strumienia bajtów `std::streambuf`.

Konwersja między sekwencjami `Elem` wartości i wielobajtowych sekwencji jest wykonywana przez obiekt klasy `Codecvt<Elem, char, std::mbstate_t>`, które spełnia wymagania aspekt standardowych konwersji kodu `std::codecvt<Elem, char, std::mbstate_t>`.

Przechowuje obiekt tej klasy szablonu:

- Wskaźnik do podstawowego buforu strumienia bajtów

- Wskaźnik do obiektu przydzielonego konwersji (który jest zwolniony, kiedy [wbuffer_convert —](../standard-library/wbuffer-convert-class.md)
