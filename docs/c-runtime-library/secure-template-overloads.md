---
title: "Przeciążenia bezpiecznych szablonów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES
- _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT
dev_langs:
- C++
helpviewer_keywords:
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES
- _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT
- secure template overloads
ms.assetid: 562741d0-39c0-485e-8529-73d740f29f8f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 92ad08738ea2c8c748ac642c5ea15f4b0a257da9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="secure-template-overloads"></a>Przeciążenia bezpiecznych szablonów
Microsoft ma przestarzały wiele C Runtime (CRT) funkcje na rzecz wersje rozszerzonymi zabezpieczeniami. Na przykład `strcpy_s` bezpieczniejsze zastępuje `strcpy`. Przestarzałe funkcje są wspólnych źródeł błędów zabezpieczeń, ponieważ nie uniemożliwiają operacje, które mogą zastąpić pamięci. Domyślnie kompilator generuje ostrzeżenie podczas korzystania z jednego z tych funkcji. CRT zapewnia przeciążenia szablonów języka C++ dla tych funkcji w celu ułatwienia przejście do bardziej bezpieczne wariantów.  
  
Na przykład następujący fragment kodu generuje ostrzeżenie, ponieważ `strcpy` jest przestarzała:  
  
```cpp  
char szBuf[10];  
strcpy(szBuf, "test"); // warning: deprecated  
```
  
Ostrzeżenia dotyczące zaniechania istnieje już informujące o tym, że kod może być niebezpieczne. Jeśli po sprawdzeniu, czy kod nie może zastąpić pamięci, masz kilka opcji. Możesz zignorować to ostrzeżenie, można określić symbol `_CRT_SECURE_NO_WARNINGS` przed instrukcje include dla CRT nagłówków, aby pominąć to ostrzeżenie, lub zaktualizować kod, aby używał `strcpy_s`:  
  
```cpp  
char szBuf[10];  
strcpy_s(szBuf, 10, "test"); // security-enhanced _s function  
```
  
Przeciążenia szablonu zapewniają dodatkowe możliwości. W przypadku definiowania `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 1, dzięki temu szablon przeciążeń standardowe funkcje CRT wywołujące bezpieczniejsze wariantów automatycznie. Jeśli `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` ma wartość 1, a następnie są niezbędne bez wprowadzania zmian w kodzie. W tle, wywołanie `strcpy` jest zmieniana na wywołanie `strcpy_s` z argumentem rozmiaru określane automatycznie.  
  
```cpp  
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1  
  
// ...  
  
char szBuf[10];  
strcpy(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")  
```  
  
Makro `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` nie ma wpływu na funkcje, których takie jak liczba, `strncpy`. Aby włączyć przeciążenia szablonów funkcji count, zdefiniuj `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` do 1. Wcześniej jednak należy się upewnić, że kod przekazuje liczbę znaków, nie rozmiar buforu (powszechnym błędem). Ponadto kod jawnie zapisuje terminatorem null końcu buforu po wywołaniu funkcji jest konieczne, jeśli bezpieczne wariant jest wywoływana. Jeśli potrzebujesz obcięcie zachowania, zobacz [_truncate —](../c-runtime-library/truncate.md).  
  
> [!NOTE]
>  Makro `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` wymaga, aby `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` jest też definiowany jako 1. Jeśli `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` jest zdefiniowany jako 1 i `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` jest zdefiniowany jako 0, aplikacja nie będzie wykonywać żadnych przeciążenia szablonu.  
  
Podczas definiowania `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` 1, umożliwia korzystanie z szablonu przeciążeń bezpiecznej wariantów (nazwy końcówką "_s"). W tym przypadku jeśli `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` ma wartość 1, a następnie co niewielkie zmiany muszą zostać wprowadzone w oryginalny kod:  
  
```cpp  
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1  
  
// ...  
  
char szBuf[10];  
strcpy_s(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")  
```  
  
 Nazwa funkcji muszą być zmienione (przez dodanie "_s"); przeciążenie szablon odpowiada on za zapewnienie argumentem rozmiaru.  
  
 Domyślnie `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` i `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` są zdefiniowane jako 0 (wyłączone) i `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` jest zdefiniowany jako 1 (włączone).  
  
 Należy pamiętać, że te szablonu overloads działa tylko dla tablic statycznych. Dynamicznie przydzielonego buforów wymagają zmiany kodu źródłowego dodatkowe. Ponowne odwiedzanie powyższe przykłady:  
  
```cpp  
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1  
  
// ...  
  
char *szBuf = (char*)malloc(10);  
strcpy(szBuf, "test"); // still deprecated; you have to change it to  
                       // strcpy_s(szBuf, 10, "test");  
```  
  
 I to:  
  
```cpp  
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1  
  
// ...  
  
char *szBuf = (char*)malloc(10);  
strcpy_s(szBuf, "test"); // doesn't compile; you have to change it to  
                         // strcpy_s(szBuf, 10, "test");  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje zabezpieczeń w CRT](../c-runtime-library/security-features-in-the-crt.md)   
 [Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)