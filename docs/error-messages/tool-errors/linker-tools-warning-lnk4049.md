---
title: Ostrzeżenie LNK4049 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4049
dev_langs:
- C++
helpviewer_keywords:
- LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b50dadc9c160ac8902cedcd60c954b565dce6e24
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4049"></a>Ostrzeżenie LNK4049 narzędzi konsolidatora
lokalnie zdefiniowany symbol "symbol" zaimportowany  
  
 Symbol zarówno został wyeksportowany z i zaimportowane do programu.  
  
 To ostrzeżenie jest generowany przez konsolidator przy deklarowaniu symbol za pomocą `__declspec(dllexport)` Klasa magazynu atrybutów w jeden obiekt pliku i odwołaj się przy użyciu `__declspec(dllimport)` atrybutu w innym.  
  
 Ostrzeżenie LNK4049 jest bardziej ogólne wersja [LNK4217 ostrzeżenia narzędzi konsolidatora](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md). Konsolidator wygeneruje ostrzeżenie LNK4049, gdy nie można określić z funkcji wystąpiło odwołanie do symbolu zaimportowane.  
  
 Typowe przypadki, w którym jest generowany LNK4049 zamiast LNK4217 są:  
  
-   Wykonywanie konsolidowania przyrostowego przy użyciu [/INCREMENTAL](../../build/reference/incremental-link-incrementally.md) opcji.  
  
-   Wykonywanie optymalizacji całego programu przy użyciu [opcję/LTCG](../../build/reference/ltcg-link-time-code-generation.md) opcji.  
  
 Aby rozwiązać LNK4049, wypróbuj jedną z następujących czynności:  
  
-   Usuń `__declspec(dllimport)` Nazwa deklaracji z deklaracja przekazująca dalej symbolu, które uruchamiane LNK4049. Symbole w obraz binarny można wyszukiwać za pomocą **DUMPBIN** narzędzia. **DUMPBIN/symbole** przełącznik wyświetla tabelą symboli COFF obrazu. Aby uzyskać więcej informacji na temat **DUMPBIN** narzędzie, zobacz [odwołanie DUMPBIN](../../build/reference/dumpbin-reference.md).  
  
-   Tymczasowe wyłączenie konsolidowania przyrostowego i optymalizacja całego programu. Ponowną kompilację aplikacji wygeneruje ostrzeżenie LNK4217, która będzie obejmować nazwę funkcji, z którego wystąpiło odwołanie do symbolu zaimportowane. Usuń `__declspec(dllimport)` deklarację z importowanych symboli i Włącz konsolidowania przyrostowego lub optymalizacji całego programu zgodnie z wymaganiami.  
  
 Mimo że wygenerowanego kodu końcowego będą działały prawidłowo, kod wygenerowany w wywołaniu funkcji importowany jest mniej wydajne niż bezpośrednie wywoływanie funkcji. To ostrzeżenie nie będą wyświetlane podczas kompilowania przy użyciu opcji [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 Aby uzyskać więcej informacji na temat Importowanie i eksportowanie danych deklaracje, zobacz [dllexport i dllimport](../../cpp/dllexport-dllimport.md).  
  
## <a name="example"></a>Przykład  
 Łączenie następujące dwa moduły wygeneruje LNK4049. Pierwszy moduł generuje obiekt zawierający pojedynczy wyeksportowanej funkcji.  
  
```  
// LNK4049a.cpp  
// compile with: /c  
  
__declspec(dllexport) int func()   
{  
   return 3;  
}  
```  
  
## <a name="example"></a>Przykład  
 Drugi moduł generuje obiekt zawierający deklaracja przekazująca dalej wyeksportowany w module pierwszy, wraz z wywołanie tej funkcji w funkcji `main` funkcji. Łączenie tego modułu z pierwszego modułu wygeneruje LNK4049. Usuwanie `__declspec(dllimport)` deklaracji rozwiąże ostrzeżenia.  
  
```  
// LNK4049b.cpp  
// compile with: /link /WX /LTCG LNK4049a.obj  
// LNK4049 expected  
  
__declspec(dllimport) int func();  
// try the following line instead  
// int func();  
  
int main()  
{  
   return func();  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Ostrzeżenie LNK4217 narzędzi konsolidatora](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md)   
 [dllexport, dllimport](../../cpp/dllexport-dllimport.md)