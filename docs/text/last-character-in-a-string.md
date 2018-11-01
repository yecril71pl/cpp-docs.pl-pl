---
title: Ostatni znak w ciągu
ms.date: 11/04/2016
helpviewer_keywords:
- last character in string
- MBCS [C++], last character in string
ms.assetid: 0a180376-4e55-41e8-9c64-539c7b6d8047
ms.openlocfilehash: 535c2e58edab49e0e2a9dbc3fce9821d5909f1c5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456267"
---
# <a name="last-character-in-a-string"></a>Ostatni znak w ciągu

Użyj następujących wskazówek:

- Dziennik zakresów bajtów nakładać się na zestaw w wielu przypadkach znaków ASCII. Można bezpiecznie bytewise skanowania dla żadnych znaków kontrolnych (mniej niż 32).

- Należy wziąć pod uwagę następujący wiersz kodu, który może być sprawdzanie, aby sprawdzić, czy ostatni znak w ciągu jest znakiem ukośnika odwrotnego:

    ```cpp
    if ( sz[ strlen( sz ) - 1 ] == '\\' )    // Is last character a '\'?
        // . . .
    ```

   Ponieważ `strlen` nie jest MBCS-aware, zwraca liczbę bajtów, nie liczbę znaków w ciągu znaków wielobajtowych. Warto również zauważyć, że w niektórych kodu stron (932, na przykład), "\\" (0x5c) jest nieprawidłowy bajt (`sz` jest ciągiem C).

   Jedno z możliwych rozwiązań jest ponownie zapisać kod w ten sposób:

    ```cpp
    char *pLast;
    pLast = _mbsrchr( sz, '\\' );    // find last occurrence of '\' in sz
    if ( pLast && ( *_mbsinc( pLast ) == '\0' ) )
        // . . .
    ```

   Ten kod używa funkcji MBCS `_mbsrchr` i `_mbsinc`. Ponieważ te funkcje są MBCS-aware, można odróżnić od "\\"znak i bajt"\\". Kod wykonuje jakąś akcję, jeśli ostatni znak w ciągu ma wartość null ('\0').

## <a name="see-also"></a>Zobacz też

[Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)<br/>
[Przypisanie znaku](../text/character-assignment.md)