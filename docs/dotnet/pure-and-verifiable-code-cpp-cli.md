---
title: Kod czysty i weryfikowalny (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- /clr compiler option [C++], verifiable assemblies
- /clr compiler option [C++], mixed assemblies
- pure MSIL [C++]
- verifiable assemblies [C++]
- verifiably type-safe code [C++]
- /clr compiler option [C++], pure assemblies
- .NET Framework [C++], pure and verifiable code
- assemblies [C++], mixed code
- verifiable assemblies [C++], about verifiable assemblies
- mixed assemblies [C++], about mixed assemblies
- pure MSIL [C++], about pure code
- assemblies [C++], verifiable code
- mixed assemblies [C++]
- assemblies [C++], pure code
ms.assetid: 9050e110-fa11-4356-b56c-665187ff871c
caps.latest.revision: "31"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9ec68a6179cd74020638aa895028942bc76e21f5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="pure-and-verifiable-code-ccli"></a>Kod czysty i weryfikowalny (C++/CLI)
Programowania .NET, Visual C++ obsługuje tworzenie trzy różne typy składników i aplikacji: mieszanych, czystych i weryfikowalnych. Wszystkie trzy są dostępne za pośrednictwem [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md) — opcja kompilatora.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat zestawy podlegające weryfikacji zobacz:  
  
-   [Porównanie funkcji mieszanych, czystych i weryfikowalnych (C + +/ CLI)](../dotnet/mixed-pure-and-verifiable-feature-comparison-cpp-cli.md)  
  
-   [Porady: Migracja do/CLR: pure (C + +/ CLI)](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)  
  
-   [Porady: tworzenie weryfikowalnych projektów C++ (C + +/ CLI)](../dotnet/how-to-create-verifiable-cpp-projects-cpp-cli.md)  
  
-   [Porady: Migracja do/CLR: safe (C + +/ CLI)](../dotnet/how-to-migrate-to-clr-safe-cpp-cli.md)  
  
-   [Używanie zestawów weryfikowalnych z programem SQL Server (C + +/ CLI)](../dotnet/using-verifiable-assemblies-with-sql-server-cpp-cli.md)  
  
-   [Najlepsze rozwiązania](../security/security-best-practices-for-cpp.md)  
  
-   [Konwertowanie projektów z trybu mieszanego na czysty język bezpośredni](../dotnet/converting-projects-from-mixed-mode-to-pure-intermediate-language.md)  
  
## <a name="mixed-clr"></a>Mieszane (/ clr)  
 Zestawy mieszane (skompilowane z **/CLR**), zawiera zarówno niezarządzanych i zarządzanych części, co umożliwia korzystanie z funkcji .NET, ale nadal zawierać kodu niezarządzanego. Dzięki temu aplikacje i składniki można zaktualizować funkcji .NET bez konieczności czy ponownego napisania całego projektu. Za pomocą języka Visual C++ można mieszać kodu zarządzane i niezarządzane w ten sposób jest wywoływana międzyoperacyjności języka C++. Aby uzyskać więcej informacji, zobacz [zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md) i [natywne i .NET współdziałanie](../dotnet/native-and-dotnet-interoperability.md).  
  
## <a name="pure-clrpure"></a>Czysty (/ clr: pure)  
 Zestawy czyste (skompilowane z **/CLR: pure**) może zawierać obu typów natywnych i zarządzanych danych, lecz tylko zarządzanego funkcji. Podobnie jak zestawy mieszane zestawy czyste umożliwiają międzyoperacyjnego z natywnych bibliotek DLL za pośrednictwem P/Invoke (zobacz [za pomocą jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)), ale nie są dostępne funkcje usługi międzyoperacyjnej modelu C++. Ponadto zestawy czyste nie można wyeksportować funkcji, które można wywołać za pomocą funkcji natywnych ponieważ punkty wejścia użycie zestawu czysty [__clrcall](../cpp/clrcall.md) konwencji wywoływania.  
  
### <a name="advantages-of-clrpure"></a>Korzyści wynikające z/CLR: pure  
  
-   Lepszą wydajność: Ponieważ zestawy czyste zawierają tylko MSIL, nie ma żadnych funkcji natywnego, a zatem żadnych zarządzanych/niezarządzanych przejść są niezbędne. (Wywołania funkcji wprowadzane za pośrednictwem P/Invoke są wyjątkiem od tej reguły).  
  
-   Rozpoznawanie elementu AppDomain: Zarządzanego funkcji i typów CLR istnieje wewnątrz `Application Domains`, co ma wpływ na ich widoczności i dostępności. Zestawy czyste rozpoznają domeny (__declspec ([elementu appdomain](../cpp/appdomain.md)) jest domniemane dla każdego typu), dostęp do ich typy i funkcje z innymi składnikami .NET jest łatwiejsze i bezpieczniejsze. W związku z tym zestawy czyste łatwiej współpracować z innymi składnikami .NET niż zestawów mieszanych.  
  
-   Ładowanie non-disk: zestawy czyste może zostać załadowany w pamięci, a nawet przesyłany strumieniowo. Jest to konieczne do użycia jako procedury składowane zestawów platformy .NET. To różni się od zestawów mieszanych, które ładowania mechanizmów, musi istnieć na dysku, aby wykonać z powodu zależności systemu Windows.  
  
-   Odbicie: Nie jest możliwe do uwzględnienia za pośrednictwem mieszanych plików wykonywalnych, zestawy czyste zapewniają obsługę Pełne odbicie. Aby uzyskać więcej informacji, zobacz [odbicia (C + +/ CLI)](../dotnet/reflection-cpp-cli.md).  
  
-   Controllability hosta: Ponieważ zestawy czyste zawierają tylko MSIL, to zachowują się bardziej przewidywalnego i elastyczne niż mieszanym zestawy, gdy jest używany w aplikacjach obsługujących środowiska CLR i modyfikowania jego zachowanie domyślne.  
  
### <a name="limitations-of-clrpure"></a>Ograniczenia/CLR: pure  
 W tej sekcji opisano funkcje, które nie są obecnie obsługiwane przez **/CLR: pure**.  
  
-   Zestawy czyste, nie można wywołać za pomocą funkcji niezarządzanej. W związku z tym zestawy czyste nie może implementować interfejsów modelu COM lub ujawnić macierzystych wywołań zwrotnych. Zestawy czyste, nie można wyeksportować funkcji za pośrednictwem __declspec(dllexport) lub. DEF, pliki. Ponadto funkcje deklarowane z \_Konwencji _clrcall nie można zaimportować za pośrednictwem \__declspec(dllimport). Funkcje w moduł macierzysty może zostać wywołana z zestawem czystego, ale zestawy czyste nie może ujawnić natywny można wywołać funkcji, dlatego udostępnianie funkcji w zestawie czysty muszą być wykonywane przez zarządzane funkcji w zestawie mieszanych. Zobacz [porady: Migracja do/CLR: pure (C + +/ CLI)](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md) Aby uzyskać więcej informacji.  
  
-   Biblioteki ATL i MFC nie są obsługiwane przez pure tryb kompilacji w programie Visual C++.  
  
-   Czysty modułów .netmodule nie są akceptowane jako dane wejściowe konsolidatora Visual C++. Pliki .obj czysty są akceptowane przez konsolidator i nadzbiorem informacji zawartych w netmodules zawiera pliki .obj. Zobacz [modułu .netmodule pliki jako dane wejściowe konsolidatora](../build/reference/netmodule-files-as-linker-input.md) Aby uzyskać więcej informacji.  
  
-   Obsługa kompilatora COM (#import) nie jest obsługiwana, ponieważ spowodowałoby to powstanie niezarządzane instrukcje w czystym zestawu.  
  
-   Liczba zmiennoprzecinkowa opcji wyrównania i obsługa wyjątków nie są zmieniane dla zestawy czyste. W związku z tym nie można użyć __declspec(align). To powoduje niektóre pliki nagłówkowe, takich jak fpieee.h, niezgodne z/CLR: pure.  
  
-   Funkcja GetLastError w PSDK zapewnić niezdefiniowane zachowanie podczas kompilowania za pomocą **/CLR: pure**.  
  
## <a name="verifiable-clrsafe"></a>Weryfikowalny (/ CLR: Safe)  
 **/CLR: Safe** zestawy podlegające weryfikacji, podobnie jak napisane w języku Visual Basic i C#, zgodne z wymaganiami, umożliwiających bieżące środowisko uruchomieniowe języka wspólnego (CLR), aby zagwarantować, że nie narusza kod generuje — opcja kompilatora ustawienia zabezpieczeń. Na przykład jeśli ustawienia zabezpieczeń zabrania składnika zapisywania na dysku, CLR można określić, czy weryfikowalny składnik spełnia to kryterium przed wykonaniem kodu. Brak obsługi CRT dla zestawy podlegające weryfikacji. (CRT obsługa jest dostępna do zestawy czyste za pomocą wersji czysty MSIL biblioteki C Runtime).  
  
 Zestawy podlegające weryfikacji oferują tych zalet w porównaniu z czysty i mieszanych zestawów:  
  
-   Większe bezpieczeństwo.  
  
-   Niektóre sytuacje wymagają go (na przykład SQL składniki).  
  
-   Coraz bardziej będzie wymagać przyszłych wersji systemu Windows, składników i aplikacje mają być możliwe do zweryfikowania.  
  
 Niedogodność jest C++ międzyoperacyjnego funkcje nie są dostępne. Zestawy podlegające weryfikacji nie może zawierać żadnych niezarządzanych funkcji lub typów danych w trybie macierzystym, nawet jeśli nie są wywoływane przez kod zarządzany.  
  
 Mimo użycia wyrazu "safe" Kompilowanie aplikacji za pomocą **/CLR: Safe** nie oznacza nie nie usterki — wystarczy oznacza CLR można sprawdzić ustawienia zabezpieczeń w czasie wykonywania.  
  
 Niezależnie od typu zestawu wywołania z zarządzanych zestawów natywnych bibliotek DLL przy użyciu elementu P/Invoke zostanie skompilowany, ale może się nie powieść w czasie wykonywania w zależności od ustawień zabezpieczeń.  
  
> [!NOTE]
>  Istnieje jeden scenariusz kodowania, które przechodzą przez kompilator, ale który spowoduje w zestawie, do którego nie można zweryfikować: wywołanie funkcji wirtualnych do wystąpienia obiektu przy użyciu operator rozpoznawania zakresów.  Na przykład: `MyObj -> A::VirtualFunction();`.  
  
## <a name="see-also"></a>Zobacz też  
 [.NET programowania w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)