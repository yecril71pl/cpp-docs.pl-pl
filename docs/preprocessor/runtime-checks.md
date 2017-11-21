---
title: runtime_checks | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.runtime_checks
- runtime_checks_CPP
dev_langs: C++
helpviewer_keywords:
- runtime_checks pragma
- pragmas, runtime_checks
ms.assetid: ae50b43f-f88d-47ad-a2db-3389e9e7df5b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ee68bfc7ddace32432f64d4325d9a4c669e0819b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="runtimechecks"></a>runtime_checks
Wyłącza lub przywraca [/RTC](../build/reference/rtc-run-time-error-checks.md) ustawienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#pragma runtime_checks( "[runtime_checks]", {restore | off} )  
```  
  
## <a name="remarks"></a>Uwagi  
 Nie można włączyć sprawdzanie za pomocą środowiska wykonawczego nie włączono opcję kompilatora. Na przykład, jeśli nie określisz rtcs, określając `#pragma runtime_checks( "s", restore)` nie dają weryfikacji ramki stosu.  
  
 **Runtime_checks** pragma musi występować poza funkcją i obowiązuje w pierwszej funkcji zdefiniowane po pragma jest widoczna. **Przywrócić** i **poza** argumenty włączyć opcje określone w *runtime_checks* lub wyłączyć.  
  
 *Runtime_checks* może być zero lub więcej parametrów pokazano w poniższej tabeli.  
  
### <a name="parameters-of-the-runtimechecks-pragma"></a>Parametry runtime_checks Pragma  
  
|Parametrów|Typ sprawdzenia dostępności środowiska wykonawczego|  
|--------------------|-----------------------------|  
|**s**|Umożliwia stosu weryfikacji (ramki).|  
|**c**|Raporty, gdy wartość jest przypisany do typu danych mniejszych powoduje utratę danych.|  
|**u**|Informuje, kiedy zmienna jest używana, zanim zostanie on zdefiniowany.|  
  
 Są to te same litery użyte z/RTC — opcja kompilatora. Na przykład:  
  
```  
#pragma runtime_checks( "sc", restore )  
```  
  
 Przy użyciu **runtime_checks** pragma z pustym ciągiem (**""**) to specjalny rodzaj dyrektywy:  
  
-   Jeśli używasz **poza** parametru włącza sprawdzanie błędów czasu wykonywania, off wymienione w powyższej tabeli.  
  
-   Jeśli używasz **przywrócić** parametru, następuje zresetowanie sprawdzanie błędów czasu wykonywania do tych, które określono/RTC — opcja kompilatora.  
  
```  
#pragma runtime_checks( "", off )  
.  
.  
.  
#pragma runtime_checks( "", restore )   
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
