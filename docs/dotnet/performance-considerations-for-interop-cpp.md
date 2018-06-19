---
title: Zagadnienia dotyczące wydajności dla międzyoperacyjności z modelem (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- /clr compiler option [C++], interop performance considerations
- platform invoke [C++], interoperability
- interop [C++], performance consideraitons
- mixed assemblies [C++], performance considerations
- interoperability [C++], performance considerations
ms.assetid: bb9a282e-c3f8-40eb-a2fa-45d80d578932
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9223c52e4ef831a9a1ff657db1a0d7859dd6ce6c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164053"
---
# <a name="performance-considerations-for-interop-c"></a>Zagadnienia dotyczące wydajności związane z międzyoperacyjnością (C++)
Ten temat zawiera wskazówki dotyczące zmniejszenia wpływu zarządzanych/niezarządzanych międzyoperacyjnego przejścia na wydajności w czasie wykonywania.  
  
 Visual C++ obsługuje te same mechanizmy współdziałanie jako innych języków .NET, takie jak Visual Basic i C# (P/Invoke), ale także międzyoperacyjnego pomocy technicznej, które są specyficzne dla języka Visual C++ (międzyoperacyjności języka C++). Wydajność kluczowych aplikacji koniecznie zrozumienie wpływu na wydajność każdego techniki międzyoperacyjnego.  
  
 Niezależnie od międzyoperacyjnego zastosowanych sekwencje specjalne przejścia, o nazwie osadzeń, wymagane są zawsze funkcją zarządzaną wywołuje niezarządzanych funkcji i na odwrót. Te sekcje Thunk są automatycznie wstawione przez kompilator języka Visual C++, ale należy pamiętać, że zbiorczo, te przejścia może być kosztowne pod względem wydajności.  
  
## <a name="reducing-transitions"></a>Zmniejszenie przejścia  
 Sposobem uniknięcia lub zmniejszyć koszt osadzeń międzyoperacyjny jest Refaktoryzuj interfejsy zaangażowane w celu zminimalizowania przejścia zarządzanych/niezarządzanych. Znacznej poprawy wydajności będzie możliwe, wybierając chatty interfejsów, które są związane z częste wywołania granicy zarządzanych/niezarządzanych. Na przykład zarządzanych funkcję, która wywołuje funkcji niezarządzanej w pętli ścisłej jest odpowiednimi kandydatami do refaktoryzacji. Jeśli sam pętli jest przenoszony do niezarządzanego po stronie lub jeśli zarządzanych alternatywą dla niezarządzanego wywołanie jest tworzony (prawdopodobnie kolejkowania dane po stronie zarządzanych i organizowanie go do niezarządzanego API jednocześnie po pętli), liczba przejścia może być obniżona logowania ificantly.  
  
## <a name="pinvoke-vs-c-interop"></a>Vs P/Invoke. międzyoperacyjność C++  
 Dla języków .NET, takie jak Visual Basic i C# metoda wyznaczonych do współpracy z natywnego składników jest P/Invoke. Ponieważ P/Invoke jest obsługiwana przez program .NET Framework, obsługuje on również Visual C++, ale Visual C++ obsługuje również własną współdziałanie, które są określone jako międzyoperacyjności języka C++. Międzyoperacyjność C++ jest preferowana przez P/Invoke, ponieważ P/Invoke nie jest bezpieczne. W związku z tym głównie zostały zgłoszone błędy w czasie wykonywania, ale międzyoperacyjności języka C++ ma także wydajności zalet w porównaniu z P/Invoke.  
  
 Obie techniki wymagają kilka kwestii, które się zdarzyć, gdy funkcja zarządzanych wywołania funkcji niezarządzanej:  
  
-   Argumenty wywołania funkcji są przekazywane z CLR dla natywnych typów.  
  
-   Konwersja bitowa niezarządzany zarządzany jest wykonywany.  
  
-   Wywołania funkcji niezarządzane (przy użyciu macierzyste wersje argumenty).  
  
-   Thunk niezarządzany zarządzany jest wykonywany.  
  
-   Zwracany typ i "out" lub "w, zewnętrzne" argumenty są przekazywane z kodu natywnego do typów CLR.  
  
 Sekcje Thunk zarządzanych/niezarządzanych są niezbędne dla międzyoperacyjności z modelem do pracy w ogóle, ale przekazywanie danych, która jest wymagana zależy od typy danych, sygnatura funkcji i użycia danych.  
  
 Przekazywanie danych z zastosowaniem międzyoperacyjności języka C++ jest to najprostsza forma możliwe: parametry są po prostu kopiowane granicy zarządzanych/niezarządzanych w sposób bitowe; Przekształcenie nie jest wykonywane w ogóle. Dla P/Invoke, to jest tylko wartość true, jeśli wszystkie parametry są proste typy danych kopiowalnych. W przeciwnym razie P/Invoke wykonuje stopniu niezawodną czynności w celu konwersji każdego parametru zarządzanego na odpowiedni typ macierzysty i odwrotnie, jeśli argumenty są oznaczone jako "out" lub "w, out".  
  
 Innymi słowy międzyoperacyjności języka C++ używa najszybszy sposób możliwe przekazywanie danych, podczas gdy najbardziej niezawodna metoda korzysta z P/Invoke. Oznacza to, że międzyoperacyjności języka C++ (w sposób typowe dla języka C++) zapewnia optymalną wydajność domyślnie, a programistę jest odpowiedzialny za adresowania czasami to zachowanie nie jest bezpieczne lub odpowiednie.  
  
 Międzyoperacyjności języka C++ w związku z tym wymaga, aby przekazywanie danych należy podać jawnie, ale zaletą jest to, że programistę będzie mógł zdecydować, co jest odpowiednia, biorąc pod uwagę rodzaj danych i jak ma być używany. Ponadto mimo że można modyfikować zachowanie przekazywanie danych P/Invoke w dostosowane w stopniu, międzyoperacyjności języka C++ umożliwia przekazywanie do dostosowania na podstawie wywołanie przez wywołanie danych. Nie jest to możliwe z P/Invoke.  
  
 Aby uzyskać więcej informacji na temat międzyoperacyjności języka C++, zobacz [za pomocą międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)