---
title: Błąd krytyczny NMAKE U1033
ms.date: 11/04/2016
f1_keywords:
- U1033
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
ms.openlocfilehash: 4511b15c84479c3531a3bea85964e2768de0181f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173390"
---
# <a name="nmake-fatal-error-u1033"></a>Błąd krytyczny NMAKE U1033

Błąd składniowy: Nieoczekiwany element "String"

Ciąg nie jest częścią prawidłowej składni pliku reguł programu make.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać ten problem, sprawdzając następujące możliwe przyczyny

1. Jeśli końcowy zestaw nawiasów ostrych ( **<<** ) dla pliku wbudowanego nie znajduje się na początku wiersza, wystąpi następujący błąd:

    ```
    syntax error : 'EOF' unexpected
    ```

1. Jeśli definicja makra w pliku reguł programu make zawierała znak równości ( **=** ) bez wcześniejszej nazwy lub jeśli zdefiniowana nazwa jest makrem, który rozwija się do Nothing, wystąpi następujący błąd:

    ```
    syntax error : '=' unexpected
    ```

1. Jeśli średnik ( **;** ) w wierszu komentarza w narzędziach. INI nie znajduje się na początku wiersza, wystąpi następujący błąd:

    ```
    syntax error : ';' unexpected
    ```

1. Jeśli plik reguł programu make został sformatowany przez Edytor tekstów, może wystąpić następujący błąd:

    ```
    syntax error : ':' unexpected
    ```
