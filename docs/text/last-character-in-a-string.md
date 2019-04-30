---
title: Ostatni znak w ciągu
ms.date: 11/04/2016
helpviewer_keywords:
- last character in string
- MBCS [C++], last character in string
ms.assetid: 0a180376-4e55-41e8-9c64-539c7b6d8047
ms.openlocfilehash: 4c99628cd12738fabb877a94cfd04a4033ee45aa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410677"
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

## <a name="see-also"></a>Zobacz także

[Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)<br/>
[Przypisanie znaku](../text/character-assignment.md)
