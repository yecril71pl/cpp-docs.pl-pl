---
title: "Porady: migracji do środowiska clr-: bezpieczne (C + +/ CLI) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- migration [C++], verifiable assemblies
- upgrading Visual C++ applications, verifiable assemblies
- verifiable assemblies [C++], migrating to
- /clr compiler option [C++], migrating to /clr:safe
ms.assetid: 75f9aae9-1dcc-448a-aa11-2d96f972f9d2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4c9d28d64b450d14ba1579597f0276cfe3a0cf39
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-migrate-to-clrsafe-ccli"></a>Porady: migracja do /clr:safe (C++/CLI)
Visual C++ może wygenerować weryfikowalny składniki przy użyciu **/CLR: Safe**, co powoduje, że kompilator, aby generować błędy dla każdego konstrukcji-weryfikowalny kod.  
  
## <a name="remarks"></a>Uwagi  
 Następujące problemy generować błędy możliwość weryfikacji:  
  
-   Typy natywne. Nawet jeśli nie jest on używany, deklaracji natywnego klasy, struktury, wskaźniki lub tablic uniemożliwi kompilacji.  
  
-   Zmienne globalne  
  
-   Wywołania funkcji do żadnych niezarządzanych biblioteka, w tym wspólne wywołania funkcji środowiska uruchomieniowego języka  
  
-   Możliwe do zweryfikowania funkcji nie może zawierać [static_cast Operator](../cpp/static-cast-operator.md) dla rzutowanie w dół. [Static_cast Operator](../cpp/static-cast-operator.md) może służyć do rzutowanie między typy pierwotne, lecz dla rzutowanie w dół, [safe_cast](../windows/safe-cast-cpp-component-extensions.md) lub rzutowania w stylu języka C (która jest zaimplementowany jako [safe_cast](../windows/safe-cast-cpp-component-extensions.md)) należy użyć.  
  
-   Możliwe do zweryfikowania funkcji nie może zawierać [reinterpret_cast Operator](../cpp/reinterpret-cast-operator.md) (lub dowolnego równoważna C rzutowanie w stylu).  
  
-   Możliwe do zweryfikowania funkcji nie można wykonać arytmetyki na [interior_ptr (C + +/ CLI)](../windows/interior-ptr-cpp-cli.md). Tylko może przypisać do niej i odwołania do niego.  
  
-   Możliwe do zweryfikowania funkcji może tylko zgłosić lub przechwycić wskaźniki do typów referencyjnych, więc typów wartości musi zostać opakowany przed wyrzucanie.  
  
-   Możliwe do zweryfikowania funkcji można wywołać tylko weryfikowalne funkcji (obejmują w taki sposób, że wywołania do środowiska CLR są niedozwolone, `AtEntry` / `AtExit`, i dlatego konstruktorów globalnych są niedozwolone).  
  
-   Nie można użyć klasy możliwe do zweryfikowania <xref:System.Runtime.InteropServices.LayoutKind>.  
  
-   Kompilowania pliku EXE, funkcja main nie można zadeklarować żadnych parametrów, więc <xref:System.Environment.GetCommandLineArgs%2A> musi być używane do pobierania argumenty wiersza polecenia.  
  
-   Nawiązywania połączenia z systemem innym niż wirtualnego funkcję wirtualną. Na przykład:  
  
    ```  
    // not_verifiable.cpp  
    // compile with: /clr  
    ref struct A {  
       virtual void Test() {}  
    };  
  
    ref struct B : A {};  
  
    int main() {  
       B^ b1 = gcnew B;  
       b1->A::Test();   // Non-virtual call to virtual function  
    }  
    ```  
  
 Ponadto następujące słowa kluczowe nie można używać w weryfikowalny kod:  
  
-   [niezarządzane](../preprocessor/managed-unmanaged.md) i [pakietu](../preprocessor/pack.md) dyrektywy pragma  
  
-   [naked](../cpp/naked-cpp.md) i [Dopasuj](../cpp/align-cpp.md) [__declspec](../cpp/declspec.md) modyfikatorów  
  
-   [__asm](../assembler/inline/asm.md)  
  
-   [__based](../cpp/based-grammar.md)  
  
-   [__try](../cpp/try-except-statement.md) i`__except`  
  
## <a name="see-also"></a>Zobacz też  
 [Kod czysty i weryfikowalny (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)