---
title: "Porady: udostępnianie kontenera STL/CLR z zestawu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, cross-assembly issues
ms.assetid: 87efb41b-3db3-4498-a2e7-f3ef8a99f04d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 84505edf0877a5ae20d28906dde7f4c709574034
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-expose-an-stlclr-container-from-an-assembly"></a>Porady: uwidacznianie kontenera STL/CLR z zestawu
Kontenery STL/CLR, takich jak `list` i `map` są zaimplementowane jako klasy ref szablonów. Ponieważ szablonów języka C++ są tworzone w czasie kompilacji, dwie klasy szablonu, które mają tę samą sygnaturę, ale w różnych zestawów są faktycznie różnych typów. Oznacza to, że nie można użyć szablonu klasy poza granicami zestawu.  
  
 Aby umożliwić udostępnianie między zestawami, kontenery STL/CLR implementować interfejs generyczny <xref:System.Collections.Generic.ICollection%601>. Przy użyciu tego interfejsu ogólnego kontenery STL/CLR mają dostęp do wszystkich języków, które obsługuje elementów ogólnych, łącznie z C++, C# i Visual Basic.  
  
 W tym temacie przedstawiono sposób wyświetlania elementów kilka kontenery STL/CLR zapisane w zestawie C++ o nazwie `StlClrClassLibrary`. Zostanie przedstawiony dwóch zestawów, aby uzyskać dostęp do `StlClrClassLibrary`. Pierwszy zestaw jest napisany w języku C++, a drugi w języku C#.  
  
 Jeśli oba zestawy są napisane w języku C++, możesz uzyskać dostęp interfejs ogólny kontenera za pomocą jego `generic_container` typedef. Na przykład, jeśli masz kontenera typu `cliext::vector<int>`, to jego interfejs ogólny: `cliext::vector<int>::generic_container`. Podobnie, Uzyskaj iteratora przez interfejs ogólny przy użyciu `generic_iterator` element typedef, jak w: `cliext::vector<int>::generic_iterator`.  
  
 Ponieważ te definicje typów są zadeklarowane w pliki nagłówkowe C++, zestawy napisanych w innych językach nie można ich używać. W związku z tym ogólny interfejs umożliwiający dostęp do `cliext::vector<int>` w języku C# lub dowolnego innego języka .NET użyj `System.Collections.Generic.ICollection<int>`. Aby przejść przez tej kolekcji, użyj `foreach` pętli.  
  
 W poniższej tabeli przedstawiono ogólny interfejs, który implementuje każdego kontenera STL/CLR:  
  
|Kontenera STL/CLR|Interfejs ogólny|  
|------------------------|-----------------------|  
|deque — < T\>|Interfejs ICollection < T\>|  
|hash_map — < K, V >|IDictionary < K, V >|  
|hash_multimap — < K, V >|IDictionary < K, V >|  
|hash_multiset — < T\>|Interfejs ICollection < T\>|  
|hash_set — < T\>|Interfejs ICollection < T\>|  
|Lista < T\>|Interfejs ICollection < T\>|  
|Mapa < K, V >|IDictionary < K, V >|  
|multimap < K, V >|IDictionary < K, V >|  
|Zestaw wielokrotny < T\>|Interfejs ICollection < T\>|  
|Ustaw < T\>|Interfejs ICollection < T\>|  
|Vector < T\>|Interfejs ICollection < T\>|  
  
> [!NOTE]
>  Ponieważ `queue`, `priority_queue`, i `stack` kontenery nie obsługują Iteratory, nie należy implementować interfejsów ogólnych i nie może być używane między zestawami.  
  
## <a name="example-1"></a>Przykład 1  
  
### <a name="description"></a>Opis  
 W tym przykładzie mamy zadeklarować klasę C++, która zawiera dane elementu członkowskiego prywatne STL/CLR. Firma Microsoft następnie zadeklarować metody publiczne, aby udzielić dostępu do kolekcji prywatnych klasy. Jak go na dwa różne sposoby, jeden dla klientów C++ i jeden dla innych klientów platformy .NET.  
  
### <a name="code"></a>Kod  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## <a name="example-2"></a>Przykład 2  
  
### <a name="description"></a>Opis  
 W tym przykładzie mamy implementuje klasy zadeklarowanej w przykładzie 1. Aby klienci używają tej biblioteki klas, używamy narzędzia manifestu **mt.exe** Aby osadzić pliku manifestu w bibliotece DLL. Aby uzyskać więcej informacji zobacz komentarze w kodzie.  
  
 Aby uzyskać więcej informacji dotyczących narzędzia manifestu i zestawy side-by-side, zobacz [tworzenie aplikacji izolowanych C/C++ i zestawy Side-by-side](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md).  
  
### <a name="code"></a>Kod  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
## <a name="example-3"></a>Przykład 3  
  
### <a name="description"></a>Opis  
 W tym przykładzie tworzymy klienta C++, który używa biblioteki klas utworzone w przykładach 1 i 2. Ten klient używa `generic_container` typedefy kontenery STL/CLR, aby przejść przez kontenery i wyświetlić ich zawartość.  
  
### <a name="code"></a>Kod  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
### <a name="output"></a>Dane wyjściowe  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
## <a name="example-4"></a>Przykład 4  
  
### <a name="description"></a>Opis  
 W tym przykładzie tworzymy klienta C#, który używa biblioteki klas utworzone w przykładach 1 i 2. Ten klient używa <xref:System.Collections.Generic.ICollection%601> metody kontenery STL/CLR, aby przejść przez kontenery i wyświetlić ich zawartość.  
  
### <a name="code"></a>Kod  
  
```  
// CsConsoleApp.cs  
// compile with: /r:Microsoft.VisualC.STLCLR.dll /r:StlClrClassLibrary.dll /r:System.dll  
  
using System;  
using System.Collections.Generic;  
using StlClrClassLibrary;  
using cliext;  
  
namespace CsConsoleApp  
{  
    class Program  
    {  
        static int Main(string[] args)  
        {  
            StlClrClass theClass = new StlClrClass();  
  
            Console.WriteLine("cliext::deque contents:");  
            ICollection<char> iCollChar = theClass.GetDequeCs();  
            foreach (char c in iCollChar)  
            {  
                Console.WriteLine(c);  
            }  
            Console.WriteLine();  
  
            Console.WriteLine("cliext::list contents:");  
            ICollection<float> iCollFloat = theClass.GetListCs();  
            foreach (float f in iCollFloat)  
            {  
                Console.WriteLine(f);  
            }  
            Console.WriteLine();  
  
            Console.WriteLine("cliext::map contents:");  
            IDictionary<int, string> iDict = theClass.GetMapCs();  
            foreach (KeyValuePair<int, string> kvp in iDict)  
            {  
                Console.WriteLine("{0} {1}", kvp.Key, kvp.Value);  
            }  
            Console.WriteLine();  
  
            Console.WriteLine("cliext::set contents:");  
            ICollection<double> iCollDouble = theClass.GetSetCs();  
            foreach (double d in iCollDouble)  
            {  
                Console.WriteLine(d);  
            }  
            Console.WriteLine();  
  
            Console.WriteLine("cliext::vector contents:");  
            ICollection<int> iCollInt = theClass.GetVectorCs();  
            foreach (int i in iCollInt)  
            {  
                Console.WriteLine(i);  
            }  
            Console.WriteLine();  
  
            return 0;  
        }  
    }  
}  
```  
  
### <a name="output"></a>Dane wyjściowe  
  
```  
cliext::deque contents:  
a  
b  
  
cliext::list contents:  
3.14159  
2.71828  
  
cliext::map contents:  
0 Hello  
1 World  
  
cliext::set contents:  
2.71828  
3.14159  
  
cliext::vector contents:  
10  
20  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja biblioteki STL/CLR](../dotnet/stl-clr-library-reference.md)