---
title: Wymagane i opcjonalne nagłówki plików
ms.date: 11/04/2016
f1_keywords:
- c.headers
helpviewer_keywords:
- include files, required in run time
- header files, required in run time
ms.assetid: f64d0bf5-e2c3-4b42-97d0-443b3d901d9f
ms.openlocfilehash: db3b05edf1496d92eaed5c7f07b9961cdde351c2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539415"
---
# <a name="required-and-optional-header-files"></a>Wymagane i opcjonalne nagłówki plików

Opis każdej procedury czasu wykonywania zawiera listę wymaganych i opcjonalnych uwzględnić, lub nagłówka (. Godz.), pliki do tej procedury. Pliki nagłówkowe wymagane konieczne w celu uzyskania deklaracji funkcji dla procedury lub definicji używany przez inny procedury metoda wywoływana wewnętrznie. Pliki opcjonalne nagłówki są zazwyczaj dołączone, aby móc korzystać z wstępnie zdefiniowanych stałych, definicje typów lub makra w tekście. W poniższej tabeli wymieniono kilka przykładów zawartości pliku w opcjonalnym nagłówku:

|Definicja|Przykład|
|----------------|-------------|
|Definicja makra|Procedury biblioteki jest implementowany jako makra, definicji makra, mogą znajdować się w pliku nagłówka innego niż plik nagłówkowy dla oryginalnego procedury. Na przykład `_toupper` — makro jest zdefiniowany w pliku nagłówkowym CTYPE. Godz., podczas funkcja `toupper` jest zadeklarowana w STDLIB. H.|
|Wstępnie zdefiniowanej stałej|Wiele procedur biblioteki można znaleźć na stałe, które są zdefiniowane w plikach nagłówkowych. Na przykład `_open` procedura używa stałych, takich jak `_O_CREAT`, która została zdefiniowana w pliku nagłówkowym FCNTL. H.|
|Definicja typu|Niektóre procedury biblioteki zwracają struktury lub użyj strukturę jako argument. Na przykład procedury we/wy strumienia użyć struktury typu `FILE`, który jest zdefiniowany w stdio —. H.|

Pliki nagłówkowe biblioteki wykonawczej zapewniają deklaracje funkcji w stylu ANSI/ISO C-standardowa zalecane. Kompilator przeprowadza kontrolę typów dla procedur odwołania, występujący po jej deklaracji funkcji skojarzonej. Deklaracje funkcji są szczególnie ważne w przypadku procedur, które zwracają wartość pewnego typu innego niż `int`, co jest ustawieniem domyślnym. Procedur, które nie należy określać ich odpowiednich zwracają wartości w jego deklarację będą uznawane za przez kompilator do zwrócenia `int`, która może spowodować nieoczekiwane rezultaty. Zobacz [sprawdzania typu](../c-runtime-library/type-checking-crt.md) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też

[Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)