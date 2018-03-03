---
title: Najlepsze praktyki optymalizacji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, optimization
- optimization, best practices
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ec12e847eef72827e11700be322fd2a2ca309037
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="optimization-best-practices"></a>Najlepsze praktyki optymalizacji
Ten dokument zawiera opis najlepsze rozwiązania dotyczące optymalizacji w programie Visual C++. Omówiono następujące zagadnienia:  
  
-   Opcje konsolidatora i kompilatora  
  
    -   optymalizacje sterowane profilem  
  
    -   Poziom optymalizacji należy użyć?  
  
    -   Liczby zmiennoprzecinkowe punktu przełączników  
  
-   Declspecs optymalizacji  
  
-   Optymalizacja Pragm  
  
-   __restrict i \__assume  
  
-   Obsługa — wewnętrzne  
  
-   Wyjątki  
  
## <a name="compiler-and-linker-options"></a>Opcje konsolidatora i kompilatora  
  
### <a name="profile-guided-optimization"></a>optymalizacje sterowane profilem  
 Visual C++ obsługuje Optymalizacja sterowana profilem — (PGO). Tego rodzaju optymalizacji używa danych profilu z ostatnich wykonań instrumentowanej wersji aplikacji do nowszej optymalizacji aplikacji. Przy użyciu PGO może zająć dużo czasu, dlatego nie może być coś, która używa każdy Deweloper, ale firma Microsoft zaleca PGO dla kompilacji ostatecznej wersji produktu. Aby uzyskać więcej informacji, zobacz [optymalizacje Profile-Guided](../../build/reference/profile-guided-optimizations.md).  
  
 Ponadto, optymalizacja Całoprogramowa (również wie jak generowanie kodu w czasie konsolidacji) i **/O1** i **/O2** udoskonalono optymalizacji. Ogólnie rzecz biorąc będzie szybsze niż w tej samej aplikacji kompilowane przy użyciu kompilatora starszych aplikacji kompilowane przy użyciu jednej z tych opcji.  
  
 Aby uzyskać więcej informacji, zobacz [/GL (optymalizacja całego programu)](../../build/reference/gl-whole-program-optimization.md) i [/O1, / O2 (Minimalizuj rozmiar, Maksymalizuj szybkość)](../../build/reference/o1-o2-minimize-size-maximize-speed.md).  
  
### <a name="which-level-of-optimization-should-i-use"></a>Poziom optymalizacji należy użyć?  
 Jeśli to możliwe ostatecznej wersji kompilacji ma być kompilowana z optymalizacje profilu. Jeśli nie jest możliwe do skompilowania z użyciem PGO, czy ze względu na niewystarczające infrastruktury dla uruchomionych kompilacji instrumentowanej lub nie ma dostępu do scenariuszy, zalecamy budynku z całej optymalizacji programu.  
  
 **/Gy** przełącznik jest również przydatne. Generuje oddzielny COMDAT dla każdej funkcji, zapewniając większą elastyczność konsolidator, jeśli chodzi o usunięcie nieużywanej Comdat i COMDAT składanie. Jedyną wadą korzystania z interfejsu **/Gy** jest, że może mieć niewielkie efektu w czasie kompilacji. W związku z tym zazwyczaj zalecane jest z niego korzystać. Aby uzyskać więcej informacji, zobacz [/Gy (Włącz funkcję łączenia na poziomie)](../../build/reference/gy-enable-function-level-linking.md).  
  
 Łączenie w środowiskach 64-bitowych, zaleca się użyć **/OPT:REF, Zapora połączenia internetowego** — opcja konsolidatora i w środowisku 32-bitowych **/OPT:REF** jest zalecane. Aby uzyskać więcej informacji, zobacz [od (optymalizacje)](../../build/reference/opt-optimizations.md).  
  
 Ponadto zaleca się generowanie symboli debugowania nawet z kompilacjami wydania zoptymalizowane. Nie efektu wygenerowanego kodu i powoduje muszą być łatwiejsze do debugowania aplikacji, jeśli wiele.  
  
### <a name="floating-point-switches"></a>Liczby zmiennoprzecinkowe punktu przełączników  
 **/Op** — opcja kompilatora został usunięty, i zostały dodane następujące cztery opcje kompilatora zajmujących się zmiennoprzecinkową optymalizacje punktu:  
  
|||  
|-|-|  
|**/ FP: precise**|To jest domyślnego zalecenia i powinny być używane w większości przypadków.|  
|**Fast**|Zalecane, jeśli wydajność jest największe znaczenie ma, na przykład w grach. Spowoduje to największą wydajność.|  
|**/ FP: strict**|Jeśli zalecane dokładne wyjątki zmiennoprzecinkowe i IEEE wymagane jest zachowanie. Spowoduje to najwolniejsze wydajności.|  
|**/ FP: except [-]**|Można używać w połączeniu z **/FP: strict** lub **/FP: precise**, ale nie **Fast**.|  
  
 Aby uzyskać więcej informacji, zobacz [/fp (określenie zachowania Floating-Point)](../../build/reference/fp-specify-floating-point-behavior.md).  
  
## <a name="optimization-declspecs"></a>Declspecs optymalizacji  
 W tej sekcji przedstawiono dwie declspecs, używane w programach w celu wydajności: `__declspec(restrict)` i `__declspec(noalias)`.  
  
 `restrict` Declspec można stosować tylko do deklaracji funkcji, które zwraca wskaźnik, takich jak`__declspec(restrict) void *malloc(size_t size);`  
  
 `restrict` Declspec jest używany w funkcji zwracających unaliased wskaźników. To słowo kluczowe jest używany do wykonania biblioteki C Runtime `malloc` ponieważ nigdy nie zwróci wartość wskaźnika, który jest już używany w bieżącym programem (chyba, że należy wykonać coś niedozwolone, takie jak użycie pamięci po został zwolniony).  
  
 `restrict` Declspec zawiera kompilator dodatkowe informacje opisujące optymalizacje kompilatora. Jeden najtrudniejsze czynności dla kompilatora określić jest jakie alias wskaźniki innych wskaźników i użycie tych informacji znacznie ułatwia kompilatora.  
  
 Warto wskazujące jest obietnicę w celu kompilatora, nie coś, który sprawdzi kompilatora. Jeśli używany przez program to `restrict` declspec niewłaściwie, program może spowodować nieprawidłowe zachowanie.  
  
 Aby uzyskać więcej informacji, zobacz [ograniczyć](../../cpp/restrict.md).  
  
 `noalias` Declspec również jest stosowane tylko do funkcji i wskazuje, że funkcja jest częściowo czystej funkcji. Częściowo czystej funkcji to taki, który odwołuje się do lub modyfikuje zmiennych lokalnych, argumentów i elementów pośrednich pierwszego stopnia argumentów. Ten declspec jest obietnicę w kompilatorze, a globals odwołuje się funkcja lub elementów pośrednich drugiego poziomu argumentów wskaźnika następnie kompilator może wygenerować kod, który dzieli aplikacji.  
  
 Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md).  
  
## <a name="optimization-pragmas"></a>Optymalizacja Pragm  
 Istnieje kilka pragm przydatne dla ułatwienia optymalizacji kodu. Pierwszy z nich omówiono `#pragma optimize`:  
  
```  
#pragma optimize("{opt-list}", on | off)  
```  
  
 Tej pragmy pozwala ustawić poziom danego optymalizacji na podstawie funkcja przez funkcję. Jest to idealne rozwiązanie w rzadkich sytuacji, gdy aplikacja awarię daną funkcję jest skompilowana przy użyciu optymalizacji. Aby wyłączyć funkcję optymalizacji dla jednej funkcji, można użyć to:  
  
```  
#pragma optimize("", off)  
int myFunc() {...}  
#pragma optimize("", on)  
```  
  
 Aby uzyskać więcej informacji, zobacz [zoptymalizować](../../preprocessor/optimize.md).  
  
 Ze Śródwierszowaniem jest jednym z najważniejszych funkcje optymalizacji, które wykonuje kompilator i tutaj omawianiu kilka pragm, które pomagają zmienić to zachowanie.  
  
 `#pragma inline_recursion`jest przydatne do określenia, czy nie ma aplikacji, aby można było wbudowanego wywołań cyklicznych. Domyślnie jest wyłączona. Skrócona rekursji o małe funkcje mogą ją włączyć. Aby uzyskać więcej informacji, zobacz [inline_recursion](../../preprocessor/inline-recursion.md).  
  
 Inny pragma przydatne dla ograniczenia głębokość ze śródwierszowaniem jest `#pragma inline_depth`. Jest to zazwyczaj przydatne w sytuacjach, w którym jest nawiązywane limit rozmiaru program lub funkcja. Aby uzyskać więcej informacji, zobacz [inline_depth](../../preprocessor/inline-depth.md).  
  
## <a name="restrict-and-assume"></a>__restrict i \__assume  
 Istnieje kilka słów kluczowych w języku Visual C++, które mogą ułatwić wydajności: [__restrict](../../cpp/extension-restrict.md) i [__assume](../../intrinsics/assume.md).  
  
 Najpierw należy zauważyć, że `__restrict` i `__declspec(restrict)` są dwa różne. Gdy są nieco powiązane, ich semantyki są różne. `__restrict`tak samo, jak jest kwalifikator typu `const` lub `volatile`, ale wyłącznie do typów wskaźnika.  
  
 Wskaźnik zmodyfikowanego z `__restrict` nazywa się *__restrict wskaźnik*. Wskaźnik __restrict jest wskaźnik, który jest możliwy tylko za pośrednictwem \__ogranicz wskaźnika. Innymi słowy, nie można użyć innego wskaźnika do uzyskiwania dostępu do danych wskazywanego przez \__ogranicz wskaźnika.  
  
 `__restrict`może być użyteczny Optymalizator Visual C++, ale jej używać z szczególną uwagę na to. Jeśli używane nieprawidłowo, optymalizator może wykonywać optymalizacji, która spowoduje awarię aplikacji.  
  
 `__restrict` Zastępuje — słowo kluczowe **porównuje** przełączyć się z poprzednimi wersjami.  
  
 Z `__assume`, deweloper może nakazuje kompilatorowi zakładają wartość niektórych zmiennej.  
  
 Na przykład `__assume(a < 5);` informuje Optymalizator, który w tym wierszu kodu zmiennej `a` jest mniejsza niż 5. Ponownie to obietnicę w celu kompilatora. Jeśli `a` jest rzeczywiście 6 w tym momencie w programie, a następnie zachowanie programu po optymalizacji kompilatora nie może być mogą spodziewać. `__assume`jest najbardziej przydatna przed instrukcji switch i/lub wyrażenia warunkowego.  
  
 Istnieją pewne ograniczenia dotyczące `__assume`. Po pierwsze, takich jak `__restrict`, jest tylko sugestia, dlatego kompilator jest bezpłatna dla go zignorować. Ponadto `__assume` obecnie działa tylko w przypadku zmiennych nierówności na stałe. Nie propaguje ono symboliczne nierówności, na przykład assume(a < b).  
  
## <a name="intrinsic-support"></a>Obsługa — wewnętrzne  
 Funkcje wewnętrzne są funkcja wywołuje którym kompilator ma wewnętrzna wiedzę o wywołaniu i zamiast wywoływania funkcji w bibliotece, jego emituje kod dla tej funkcji. Intrin.h pliku nagłówka znajdujący się w < Installation_Directory > \VC\include\intrin.h zawiera wszystkie dostępne funkcje wewnętrzne dla każdego z trzech obsługiwanych platform (x 86, x64 i ARM).  
  
 Funkcje wewnętrzne pozwalają programistę na Przejdź dogłębną analizę kodu bez konieczności użycia zestawu. Istnieje kilka korzyści wynikające z używania funkcji wewnętrznych:  
  
1.  Kod jest przenośną. Niektóre funkcje wewnętrzne są dostępne w wielu architektury Procesora.  
  
2.  Kod jest łatwiejsze do czytania, ponieważ kod nadal jest napisany w języku C/C++.  
  
3.  Kod pobiera korzyści optymalizacje kompilatora. Jak kompilator pobiera lepsze, poprawia generowanie kodu dla funkcji wewnętrznych.  
  
 Aby uzyskać więcej informacji, zobacz [funkcje wewnętrzne kompilatora](../../intrinsics/compiler-intrinsics.md).  
  
## <a name="exceptions"></a>Wyjątki  
 Brak wydajności związanych z używaniem wyjątków trafień. Niektóre ograniczenia są wprowadzane podczas przy użyciu bloków try, które wstrzymywania wykonywanie niektórych optymalizacje kompilatora. Na x86 platformy, z którymi jest spadek wydajności dodatkowych z spróbuj bloki z powodu stanu dodatkowe informacje, które musi zostać wygenerowany podczas wykonywania kodu. Na platformach 64-bitowych bloków nie obniżenia wydajności tyle, ale po jest zgłaszany wyjątek, proces znajdowania obsługi i odwijanie stosu może być kosztowne.  
  
 W związku z tym zaleca się unikać wprowadzania bloków try/catch do kodu, który nie jest konieczne go. Jeśli należy użyć wyjątki, użyj synchroniczne wyjątków, jeśli to możliwe. Aby uzyskać więcej informacji, zobacz [strukturalnych obsługi wyjątków (C/C++)](../../cpp/structured-exception-handling-c-cpp.md).  
  
 Ponadto zgłaszają wyjątki dla tylko wyjątku. Używanie wyjątków do przepływu sterowania ogólne prawdopodobnie spowoduje obniżenie wydajności.  
  
## <a name="see-also"></a>Zobacz też  
 [Optymalizacja kodu](../../build/reference/optimizing-your-code.md)