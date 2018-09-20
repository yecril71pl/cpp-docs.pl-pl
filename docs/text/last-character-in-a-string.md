---
title: Ostatni znak w ciągu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- last character in string
- MBCS [C++], last character in string
ms.assetid: 0a180376-4e55-41e8-9c64-539c7b6d8047
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e207ec1d5489a629b765d398e26ac7c07771d0da
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384991"
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