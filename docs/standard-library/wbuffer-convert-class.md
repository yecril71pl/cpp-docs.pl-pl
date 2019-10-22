---
title: wbuffer_convert — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocmon/stdext::cvt::wbuffer_convert
helpviewer_keywords:
- wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
ms.openlocfilehash: 8de0091af93120290105ce7603fae5acff257b76
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688543"
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

|Parametr|Opis|
|---------------|-----------------|
|*Codecvt*|Zestaw reguł [ustawień regionalnych](../standard-library/locale-class.md) , który reprezentuje obiekt konwersji.|
|*Elem*|Typ elementu dwubajtowego.|
|*Cech*|Cechy skojarzone z *elem*.|

## <a name="remarks"></a>Uwagi

Ten szablon klasy opisuje bufor strumienia, który kontroluje transmisję elementów typu `_Elem`, których cechy znakowe są opisane przez klasę `Traits`, do i z bufora strumienia bajtów typu `std::streambuf`.

Konwersja między sekwencją wartości `Elem` i sekwencji wielobajtowych jest wykonywana przez obiekt klasy `Codecvt<Elem, char, std::mbstate_t>`, który spełnia wymagania standardowego aspektu konwersji kodu `std::codecvt<Elem, char, std::mbstate_t>`.

Obiekt tego szablonu klasy przechowuje:

- Wskaźnik do buforu strumienia bajtów źródłowych

- Wskaźnik do przydzielony obiekt konwersji (zwolniony, gdy [wbuffer_convert](../standard-library/wbuffer-convert-class.md)
