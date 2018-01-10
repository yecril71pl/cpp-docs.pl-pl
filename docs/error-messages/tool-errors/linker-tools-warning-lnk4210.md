---
title: "Ostrzeżenie LNK4210 narzędzi konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4210
dev_langs: C++
helpviewer_keywords: LNK4210
ms.assetid: db48cff8-a2be-4a77-8d03-552b42c228fa
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e4e2d596527b60735b42fb4edfff6f36d0be808d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4210"></a>Ostrzeżenie LNK4210 narzędzi konsolidatora  
  
> sekcja *sekcji* istnieje; może być nieobsługiwany statyczne inicjatory lub terminatory  
  
Kodu wprowadziła statyczne inicjatory lub terminatory, ale kod uruchomienia biblioteki VCRuntime lub jego odpowiednik (co wymaga, aby uruchomić statyczne inicjatory lub terminatory) nie jest uruchamiane podczas uruchamiania aplikacji. Oto kilka przykładów kodu, który wymaga statyczne inicjatory lub terminatory:  
  
-   Zmienna klasy globalnej Konstruktor, destruktor lub tabeli funkcji wirtualnych.  
  
-   Zmienna globalna zainicjowany przy użyciu stałej się w czasie kompilacji.  
  
Aby rozwiązać ten problem, wypróbuj jedną z następujących czynności:  
  
-   Usuń cały kod z statyczne inicjatory.  
  
-   Nie używaj [/noentry](../../build/reference/noentry-no-entry-point.md). Po usunięciu/noentry także mogą wymagać usunięcia [/nodefaultlib](../../build/reference/nodefaultlib-ignore-libraries.md) z wiersza polecenia konsolidatora.  
  
-   Jeśli kompilację używa/MT, dodać libcmt.lib, libvcruntime.lib i libucrt.lib z wierszem polecenia konsolidatora. Jeśli kompilację używa /MTd, należy dodać biblioteki libcmtd.lib, vcruntimed.lib i libucrtd.lib.  
  
-   Podczas przenoszenia z/CLR: pure kompilacji/CLR, Usuń [/Entry](../../build/reference/entry-entry-point-symbol.md) opcję z linii konsolidatora. To umożliwia Inicjalizacja CRT oraz umożliwia statyczne inicjatory do wykonania podczas uruchamiania aplikacji.  
  
 [/GS](../../build/reference/gs-buffer-security-check.md) — opcja kompilatora wymaga inicjowania przez `__security_init_cookie` funkcji. Inicjowanie tej znajduje się domyślnie w kodzie uruchamiania VCRuntime biblioteki, który jest uruchamiany w `_DllMainCRTStartup`.  
  
-   Projekt został zbudowany przy użyciu/Entry, a/Entry jest przekazywana funkcja innych niż `_DllMainCRTStartup`, należy wywołać funkcję `_CRT_INIT` zainicjować CRT. Jeśli biblioteki DLL używa/GS, wymaga statyczne inicjatory lub jest wywoływany w kontekście kodu MFC lub ATL tego samego połączenia jest niewystarczająca. Zobacz [biblioteki dll i Visual C++ zachowanie biblioteki wykonawczej](../../build/run-time-library-behavior.md) Aby uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)