---
title: 'główne: uruchamianie programu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- vc.main.startup
- _tmain
dev_langs:
- C++
helpviewer_keywords:
- program startup [C++]
- entry points, program
- wmain function
- _tmain function
- startup code, main function
- main function, program startup
ms.assetid: f9581cd6-93f7-4bcd-99ec-d07c3c107dd4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f78a122837fc2cb9a89083d5be8fd2b488c1772
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939227"
---
# <a name="main-program-startup"></a>main: uruchamianie programu
Specjalną funkcję o nazwie `main` jest punktem początkowym wykonanie wszystkich programów C i C++. Jeśli jesteś pisanie kodu, która jest zgodna [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] modelu programowania, można użyć `wmain`, która jest wersją znaków dwubajtowych z `main`.  
  
 `main` Funkcja nie jest wstępnie zdefiniowana przez kompilator. Wymagane jest podanie tekstu programu.  
  
 Składnia deklaracji `main` jest  
  
```cpp 
int main();  
```  
  
 lub, opcjonalnie,  
  
```cpp 
int main(int argc, char *argv[], char *envp[]);  
```  
  
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Składnia deklaracji `wmain` jest następująca:  
  
```cpp 
int wmain( );  
```  
  
 lub, opcjonalnie,  
  
```cpp 
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);  
```  
  
 Można również użyć `_tmain`, która została zdefiniowana w TCHAR.h. `_tmain` jest rozpoznawana jako `main` , chyba że _UNICODE zdefiniowano. W takim przypadku `_tmain` jest rozpoznawana jako `wmain`.  
  
 Alternatywnie `main` i `wmain` funkcje mogą być zadeklarowane jako zwracanie **void** (nie zwraca wartości). Jeśli zadeklarujesz `main` lub `wmain` powrotu **void**, nie można zwrócić kod wyjścia procesu nadrzędnego lub systemu operacyjnego za pomocą [zwracają](../cpp/return-statement-in-program-termination-cpp.md) instrukcji. Do zwrócenia wyjście kodu, gdy `main` lub `wmain` jest zadeklarowany jako **void**, należy użyć [wyjść](../cpp/exit-function.md) funkcji.  
  
**END specyficzny dla Microsoft**  
 Typy dla `argc` i `argv` są definiowane przez język. Nazwy `argc`, `argv`, i `envp` są tradycyjne, ale nie są wymagane przez kompilator. Aby uzyskać więcej informacji i obejrzeć przykład, zobacz [definicje argumentu](../cpp/argument-definitions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Keywords](../cpp/keywords-cpp.md)   
 [Korzystanie z wmain zamiast main](../cpp/using-wmain-instead-of-main.md)   
 [Ograniczenia funkcji Main](../cpp/main-function-restrictions.md)   
 [Analizowanie argumentów wiersza polecenia języka C++](../cpp/parsing-cpp-command-line-arguments.md)
