---
title: '&lt;codecvt —&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- codecvt
- <codecvt>
dev_langs:
- C++
helpviewer_keywords:
- codecvt header
ms.assetid: d44ee229-00d5-4761-9b48-0c702122789d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 973f183980e89ac0be268e5cbbec42de83a378f4
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965818"
---
# <a name="ltcodecvtgt"></a>&lt;codecvt&gt;

Definiuje kilka klas szablonów, które opisują obiektów na podstawie szablonu klasy [codecvt](../standard-library/codecvt-class.md). Te obiekty mogą pełnić rolę [zestawów reguł ustawień regionalnych](../standard-library/locale-class.md#facet_class) umożliwiające sterowanie konwersji między sekwencjami wartości typu `Elem` i sekwencjami wartości typu **char**.

## <a name="syntax"></a>Składnia

```cpp
#include <codecvt>

```

## <a name="remarks"></a>Uwagi

Zestawy reguł ustawień regionalnych, zadeklarowany w tym nagłówku konwersji między kilka kodowania znaków. Dla znaków dwubajtowych (przechowywanej w ramach programu w stałym rozmiarze liczb całkowitych):

- UCS-4 jest zakodowane w Unicode (ISO 10646) w ramach programu jako liczba całkowita 32-bitowych.

- UCS-2 jest Unicode zakodowanych w ramach programu jako 16-bitową liczbę całkowitą.

- UTF-16 jest zakodowane w ramach programu jako jednej lub dwóch 16-bitowych liczb całkowitych w Unicode. (Zwróć uwagę, że nie spełnia wszystkie wymagania znaków dwubajtowych zakodowany dla standardowej C lub Standard C++. Niemniej jednak jest powszechnie używany jako takie.)

Dla strumieni bajtów (przechowywane w pliku, przesyłane jako sekwencja bajtów lub przechowywane w ramach programu w tablicy **char**):

- UTF-8 są zakodowane w ramach strumienia bajtów jako co najmniej jeden bajtów 8 bitowa z kolejnością bajtów deterministyczne w Unicode.

- UTF-16LE jest zakodowany w ramach strumienia bajtów w formacie UTF-16 Unicode przy użyciu każdego 16-bitową liczbę całkowitą, przedstawione jako dwa bajty 8 bitowa, mniej znaczący bajt najpierw.

- UTF-16BE jest zakodowany w ramach strumienia bajtów w formacie UTF-16 Unicode przy użyciu każdego 16-bitową liczbę całkowitą, przedstawione jako dwa bajty 8 bitowa, bardziej znaczący bajt najpierw.

### <a name="enumerations"></a>Wyliczenia

|||
|-|-|
|[codecvt_mode](../standard-library/codecvt-enums.md#codecvt_mode)|Określa informacje o konfiguracji dla zestawów reguł ustawień regionalnych.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[codecvt_utf8](codecvt-utf8-class.md)|Reprezentuje zestaw reguł ustawień regionalnych, który wykonuje konwersję między zakodowanymi w formacie UCS-2 lub UCS-4 znaki dwubajtowe, a strumień bajtów zakodowanymi w formacie UTF-8.|
|[codecvt_utf8_utf16](codecvt-utf8-utf16-class.md)|Reprezentuje zestaw reguł ustawień regionalnych, który wykonuje konwersję między zakodowanymi w formacie UTF-16 znaków dwubajtowych i strumień bajtów zakodowanymi w formacie UTF-8.|
|[codecvt_utf16](codecvt-utf16-class.md)|Reprezentuje zestaw reguł ustawień regionalnych, który wykonuje konwersję między zakodowanymi w formacie UCS-2 lub UCS-4 znaków dwubajtowych i zakodowanymi w formacie UTF-16LE lub UTF-16BE strumień bajtów.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<codecvt >

**Namespace:** stdt

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
