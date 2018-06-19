---
title: 'Porady: diagnozowanie i usuwanie problemów ze zgodnością zestawu (C + +/ CLI) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- versioning, diagnosing conflicts
- versioning
- exceptions, diagnosing odd behavior
- compatibility, between assemblies
ms.assetid: 297c71e3-04a8-4d24-a5dc-b04a2c5cc6fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d4440ab455aff8922c108cdb35cff041cd67f56d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33133431"
---
# <a name="how-to-diagnose-and-fix-assembly-compatibility-problems-ccli"></a>Porady: diagnozowanie i usuwanie problemów ze zgodnością zestawu (C++/CLI)
W tym temacie opisano, co może się zdarzyć, gdy wersja zestawu odwołania w czasie kompilacji nie pasuje do wersji zestawu odwołania w czasie wykonywania oraz sposób uniknąć tego problemu.  
  
 Podczas kompilowania zestawu innych zestawów odwołania mogą dotyczyć z `#using` składni. Podczas kompilacji te zestawy są dostępne przez kompilator. Informacje z tych zestawów są używane do podejmowania decyzji o optymalizacji.  
  
 Jednak jeśli przywoływanego zestawu jest zmienione i ponownie skompilowana, a nie zostanie ponownie skompilowana odwołaniem do zestawu, który jest zależne od tego, zestawy mogą nie być zgodne. Decyzje dotyczące optymalizacji, które były prawidłowe w pierwszym mogą być nieprawidłowe w odniesieniu do nowej wersji zestawu. Z powodu niezgodności te mogą wystąpić różne błędy środowiska wykonawczego. Nie ma żadnych określony wyjątek, który zostanie wygenerowany w takich przypadkach. Błąd jest zgłaszany w czasie wykonywania sposób zależy od rodzaju zmiany kodu, który spowodował problem.  
  
 Te błędy nie powinien być problemem w kodzie produkcyjnym końcowego, pod warunkiem, cała aplikacja zostanie odtworzony do pełnej wersji produktu. Zestawy, które są wydawane publicznie powinien być oznaczony przez numer wersji oficjalnej, który zapewni uniknąć tych problemów. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji zestawu](/dotnet/framework/app-domains/assembly-versioning).  
  
### <a name="diagnosing-and-fixing-an-incompatibility-error"></a>Diagnozowania i rozwiązywania błąd niezgodności  
  
1.  Jeśli występują wyjątki środowiska uruchomieniowego lub innych błędów, które występują w kodzie, który odwołuje się do innego zestawu i mieć żadnych innych zidentyfikowanych Przyczyna może dotyczących zestawu nieaktualny.  
  
2.  Najpierw izolowanie i Odtwórz wyjątek lub inny warunek błędu. Powinna być odtworzenia problemu, który występuje z powodu wyjątku nieaktualne.  
  
3.  Sprawdź sygnatury czasowej dowolne zestawy, do których odwołuje się do aplikacji.  
  
4.  Jeśli nowsza niż sygnatura czasowa ostatniej kompilacji aplikacji sygnatury dowolne zestawy, do którego istnieje odwołanie, aplikacja jest nieaktualny. W takim przypadku ponownie skompilować aplikację z najnowszych zestawu i wprowadź wymagane zmiany kodu.  
  
5.  Uruchom ponownie aplikację, należy wykonać czynności, które odtworzenia problemu, a następnie sprawdź, czy wyjątek nie występuje.  
  
## <a name="example"></a>Przykład  
 Następujący program zilustrowano problem, zmniejszając dostępność metody, a próby uzyskania dostępu do tej metody w innym zestawie bez konieczności ponownego kompilowania. Spróbuj skompilować `changeaccess.cpp` pierwszy. Jest to przywoływanego zestawu, co spowoduje zmianę. Następnie skompilować `referencing.cpp`. Kompilacja zakończy się pomyślnie. Teraz Zmniejsz dostępność wywołaną metodę. Skompiluj ponownie `changeaccess.cpp` z flagą `/DCHANGE_ACCESS`. Dzięki temu ta metoda chronionych, a nie prywatnego, więc może ona już zostać wywołana legalnie. Bez konieczności ponownego kompilowania `referencing.exe`, uruchom ponownie aplikację. Wystąpił wyjątek <xref:System.MethodAccessException> spowoduje.  
  
```  
// changeaccess.cpp  
// compile with: /clr:safe /LD  
// After the initial compilation, add /DCHANGE_ACCESS and rerun  
// referencing.exe to introduce an error at runtime. To correct  
// the problem, recompile referencing.exe  
  
public ref class Test {  
#if defined(CHANGE_ACCESS)  
protected:  
#else  
public:  
#endif  
  
  int access_me() {  
    return 0;  
  }  
  
};  
  
```  
  
```  
// referencing.cpp  
// compile with: /clr:safe   
#using <changeaccess.dll>  
  
// Force the function to be inline, to override the compiler's own  
// algorithm.  
__forceinline  
int CallMethod(Test^ t) {  
  // The call is allowed only if access_me is declared public  
  return t->access_me();  
}  
  
int main() {  
  Test^ t = gcnew Test();  
  try  
  {  
    CallMethod(t);  
    System::Console::WriteLine("No exception.");  
  }  
  catch (System::Exception ^ e)  
  {  
    System::Console::WriteLine("Exception!");  
  }  
  return 0;  
}  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [#using — dyrektywa](../preprocessor/hash-using-directive-cpp.md)   
 [Typy zarządzane (C++/CLI)](../dotnet/managed-types-cpp-cli.md)