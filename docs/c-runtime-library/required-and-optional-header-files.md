---
title: Wymagane i opcjonalne nagłówki plików
ms.date: 11/04/2016
f1_keywords:
- c.headers
helpviewer_keywords:
- include files, required in run time
- header files, required in run time
ms.assetid: f64d0bf5-e2c3-4b42-97d0-443b3d901d9f
ms.openlocfilehash: 8d1547ae7dd3b6adb33271e93e85022f04859886
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211609"
---
# <a name="required-and-optional-header-files"></a>Wymagane i opcjonalne nagłówki plików

Opis każdej procedury wykonawczej zawiera listę elementów wymaganych i opcjonalnych dołączania lub nagłówka (. H), pliki dla tej procedury. Wymagane pliki nagłówkowe muszą być dołączone w celu uzyskania deklaracji funkcji dla procedury lub definicji używanej przez inną procedurę nazywaną wewnętrznie. Opcjonalne pliki nagłówkowe zwykle są uwzględniane w celu wykorzystania wstępnie zdefiniowanych stałych, definicji typów lub makr wbudowanych. W poniższej tabeli wymieniono przykłady opcjonalnego pliku nagłówka:

|Definicja|Przykład|
|----------------|-------------|
|Definicja makra|Jeśli procedura biblioteki jest zaimplementowana jako makro, definicja makra może znajdować się w pliku nagłówkowym innym niż plik nagłówkowy oryginalnej procedury. Na przykład `_toupper` makro jest zdefiniowane w pliku nagłówka CType. H, podczas gdy funkcja `toupper` jest zadeklarowana w STDLIB. C.|
|Wstępnie zdefiniowana stała|Wiele procedur bibliotek odwołuje się do stałych, które są zdefiniowane w plikach nagłówkowych. Na przykład `_open` procedura używa stałych, takich jak `_O_CREAT` , które są zdefiniowane w pliku nagłówka fcntl. C.|
|Definicja typu|Niektóre procedury biblioteki zwracają strukturę lub przyjmują strukturę jako argument. Na przykład procedury przesyłania strumieniowego danych wejściowych/wyjściowych używają struktury typu `FILE` , która jest zdefiniowana w stdio. C.|

Pliki nagłówkowe biblioteki wykonawczej zawierają deklaracje funkcji w standardowym zalecanym stylu ANSI/ISO C. Kompilator wykonuje sprawdzanie każdego odwołania do procedury, które występuje po deklaracji skojarzonej funkcji. Deklaracje funkcji są szczególnie ważne w przypadku procedur zwracających wartość jednego typu innego niż **`int`** , który jest wartością domyślną. Procedury, które nie określają odpowiedniej wartości zwracanej w swojej deklaracji, zostaną uznane za przez kompilator, aby zwracały **`int`** , co może spowodować nieoczekiwane wyniki. Zobacz [sprawdzanie typu](../c-runtime-library/type-checking-crt.md) , aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz także

[Funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md)
