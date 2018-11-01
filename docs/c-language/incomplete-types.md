---
title: Niekompletne typy
ms.date: 11/04/2016
helpviewer_keywords:
- void keyword [C], incomplete
- types [C], incomplete
- incomplete types
- unions, incomplete
- arrays [C], incomplete types
- void keyword [C]
- structures, incomplete
ms.assetid: 01bc0cf6-9fa7-458c-9371-ecbe54ea6aee
ms.openlocfilehash: 9f0df4c28fc0da860d5a903b3f2833a328312dd7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50433504"
---
# <a name="incomplete-types"></a>Niekompletne typy

*Niekompletnego typu* to typ, który opisuje identyfikator, ale nie zawiera informacje potrzebne do określenia rozmiaru identyfikatora. Może być niekompletnym typem:

- Typ struktury elementów członkowskich, których jeszcze nie określono.

- Typ Unii członków, których jeszcze nie określono.

- Typ tablicy wymiaru, którego jeszcze nie określono.

**Void** typ jest niekompletnego typu, który nie może zostać zakończona. Aby ukończyć niekompletnego typu, należy określić brakujące informacje. Poniższe przykłady pokazują, jak utworzyć i wykonać niekompletnych typów.

- Aby utworzyć typ struktury niekompletna, należy zadeklarować typ struktury bez określenia jej członków. W tym przykładzie `ps` punktów wskaźnika do typu niekompletnego struktury o nazwie `student`.

    ```C
    struct student *ps;
    ```

- Aby ukończyć typ struktury niekompletna, należy zadeklarować ten sam typ struktury później w tym samym zakresie z jej elementów członkowskich, które określono w

    ```C
    struct student
    {
        int num;
    }                   /* student structure now completed */
    ```

- Aby utworzyć niepełny typ tablicy, należy zadeklarować typu tablicowego bez określenia jego licznik powtórzeń. Na przykład:

    ```C
    char a[];  /* a has incomplete type */
    ```

- Ukończenie niepełny typ tablicy, należy zadeklarować z jego licznika powtórzeń, określone w tej samej nazwie w dalszej części tego samego zakresu

    ```C
    char a[25]; /* a now has complete type */
    ```

## <a name="see-also"></a>Zobacz też

[Deklaracje i typy](../c-language/declarations-and-types.md)