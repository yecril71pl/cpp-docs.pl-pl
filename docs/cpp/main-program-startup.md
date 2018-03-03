---
title: 'main: uruchamianie programu | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1fbb3d19101358012df795000907a0b3e8139601
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="main-program-startup"></a>main: uruchamianie programu
Specjalnych funkcji o nazwie `main` jest punktem początkowym wykonywania dla wszystkich programów C i C++. Jeśli jesteś pisanie kodu, która jest zgodna [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] modelu programowania, można użyć `wmain`, która jest wersja znaków dwubajtowych `main`.  
  
 `main` Funkcja nie jest wstępnie zdefiniowana przez kompilator. Musi zostać dostarczony w tekście program.  
  
 Składnia deklaracji `main` jest  
  
```  
int main();  
```  
  
 lub, opcjonalnie,  
  
```  
int main(int argc, char *argv[], char *envp[]);  
```  
  
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Składnia deklaracji `wmain` wygląda następująco:  
  
```  
int wmain( );  
```  
  
 lub, opcjonalnie,  
  
```  
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);  
```  
  
 Można również użyć `_tmain`, która jest zdefiniowana w pliku TCHAR.h. `_tmain`jest rozpoznawana jako `main` Jeśli _unicode — nie jest zdefiniowany. W takim przypadku `_tmain` jest rozpoznawana jako `wmain`.  
  
 Alternatywnie `main` i `wmain` funkcje mogą być deklarowane jako zwracanie `void` (Brak wartości zwracanej). W przypadku `main` lub `wmain` jako zwracanie `void`, nie można zwrócić kod zakończenia procesu nadrzędnego lub systemu operacyjnego za pomocą [zwracać](../cpp/return-statement-in-program-termination-cpp.md) instrukcji. Aby powrócić zakończenia kodu, gdy `main` lub `wmain` jest zadeklarowany jako `void`, należy użyć [zakończyć](../cpp/exit-function.md) funkcji.  
  
**KOŃCOWY określonych firmy Microsoft**  
 Typy dla `argc` i `argv` są definiowane przez język. Nazwy `argc`, `argv`, i `envp` są tradycyjne, ale nie są wymagane przez kompilator. Aby uzyskać więcej informacji i przykład zobacz [definicje argumentu](../cpp/argument-definitions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [Korzystanie z wmain zamiast main](../cpp/using-wmain-instead-of-main.md)   
 [Ograniczenia funkcji main](../cpp/main-function-restrictions.md)