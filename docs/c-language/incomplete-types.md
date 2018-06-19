---
title: Niekompletne typy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- void keyword [C], incomplete
- types [C], incomplete
- incomplete types
- unions, incomplete
- arrays [C], incomplete types
- void keyword [C]
- structures, incomplete
ms.assetid: 01bc0cf6-9fa7-458c-9371-ecbe54ea6aee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c357364280244ea62e90badcb91f76138e81a990
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384375"
---
# <a name="incomplete-types"></a>Niekompletne typy
Niekompletny typ jest typem, który opisuje identyfikator, ale nie zawiera informacje potrzebne do określenia rozmiaru identyfikatora. "Niekompletnego typu" może być:  
  
-   Typ struktury elementów członkowskich, których jeszcze nie zostało określone.  
  
-   Typ union członków, których jeszcze nie zostało określone.  
  
-   Typ tablicy wymiaru, którego jeszcze nie zostało określone.  
  
 Typu void jest niekompletny typ, który nie może zostać zakończona. Aby ukończyć niekompletnego typu, należy określić brakujące informacje. Poniższe przykłady przedstawiają sposób tworzenia i ukończyć niekompletne typy.  
  
-   Aby utworzyć typ struktury niekompletna, należy zadeklarować typ struktury bez określenia jego elementów członkowskich. W tym przykładzie `ps` wskaźnik wskazuje na typ struktury niekompletne o nazwie `student`.  
  
    ```  
    struct student *ps;  
    ```  
  
-   Aby ukończyć typ struktury niekompletne, zadeklarowana tej samej struktury później w tym samym zakresie z jego elementów członkowskich określonych w  
  
    ```  
    struct student  
    {  
        int num;  
    }                   /* student structure now completed */  
    ```  
  
-   Aby utworzyć niepełny typ tablicy, należy zadeklarować typ tablicowy bez określenia jego liczbę powtórzeń. Na przykład:  
  
    ```  
    char a[];  /* a has incomplete type */  
    ```  
  
-   Aby ukończyć niepełny typ tablicy, zadeklarować takiej samej nazwie później w tym samym zakresie z jego liczbę powtórzeń określone w  
  
    ```  
    char a[25]; /* a now has complete type */  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje i typy](../c-language/declarations-and-types.md)