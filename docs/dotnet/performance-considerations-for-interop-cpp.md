---
title: Zagadnienia dotyczące wydajności związane z międzyoperacyjnością (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], interop performance considerations
- platform invoke [C++], interoperability
- interop [C++], performance consideraitons
- mixed assemblies [C++], performance considerations
- interoperability [C++], performance considerations
ms.assetid: bb9a282e-c3f8-40eb-a2fa-45d80d578932
ms.openlocfilehash: 29dbfa6465f6bcbcf4d0618b1820e59a8edbd3a3
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447252"
---
# <a name="performance-considerations-for-interop-c"></a>Zagadnienia dotyczące wydajności związane z międzyoperacyjnością (C++)

Ten temat zawiera wskazówki w celi zmniejszenia wpływu zarządzanych/niezarządzanych międzyoperacyjny przejścia na wydajności w czasie wykonywania.

Visual C++ obsługuje te same mechanizmy współdziałanie jako innych językach .NET, takich jak Visual Basic i C# (P/Invoke), ale udostępnia również międzyoperacyjny pomocy technicznej, które są specyficzne dla języka Visual C++ (międzyoperacyjności języka C++). Wydajność krytycznych aplikacji ważne jest zrozumienie wpływu na wydajność każdej techniki międzyoperacyjnego.

Niezależnie od tego, międzyoperacyjny techniki używane sekwencje specjalne przejścia, o nazwie sekcje Thunk, wymagane jest każdej funkcji zarządzanej wywołuje niezarządzanych funkcji i odwrotnie. Te sekcje Thunk są wprowadzane automatycznie przez firmę Microsoft C++ kompilator, ale ważne jest, aby pamiętać, że łącznie, te przejścia może być kosztowna pod względem wydajności.

## <a name="reducing-transitions"></a>Zmniejszenie przejścia

Jednym ze sposobów uniknięcia lub zmniejszyć koszt międzyoperacyjny sekcje Thunk jest Refaktoryzacja zaangażowane w celu zminimalizowania przejścia zarządzanych/niezarządzanych interfejsów. Znacznej poprawy wydajności jest możliwe dzięki systemowi chatty — interfejsy, które zaangażowany częste wywołania przez granicę zarządzanych/niezarządzanych. Funkcji zarządzanej, która wywołuje niezarządzanej funkcji w pętli, na przykład, jest dobrym kandydatem do refaktoryzacji. Jeśli pętla, sama jest przenoszony do niezarządzanym lub jeśli alternatywnego kodu zarządzanego do niezarządzanego wywołanie zostanie utworzony (prawdopodobnie kolejkowania dane po stronie zarządzanej i zorganizowanie ich do niezarządzanego interfejsu API wszystkie na raz po pętli), liczba przejścia może być obniżona logowania ificantly.

## <a name="pinvoke-vs-c-interop"></a>Vs P/Invoke. międzyoperacyjność C++

W językach .NET, takich jak Visual Basic i C# dla określonej metody współdziałanie ze składnikami macierzystymi jest P/Invoke. P/Invoke jest obsługiwany przez program .NET Framework, Visual C++ obsługuje ona również, ale Visual C++ obsługuje również swój własny współdziałanie, który jest określany jako międzyoperacyjności języka C++. Międzyoperacyjności języka C++ jest preferowana za pośrednictwem metody P/Invoke, ponieważ metody P/Invoke nie jest bezpieczny. W wyniku błędy przede wszystkim są zgłaszane w czasie wykonywania, ale międzyoperacyjności języka C++ jest również korzyści związanych z wydajnością za pośrednictwem metody P/Invoke.

Obu tych technik wymagają kilka rzeczy, które ma być wykonywana po każdym zarządzanym funkcja wywołuje niezarządzanej funkcji:

- Argumenty wywołania funkcji są przekazywane z CLR w natywnych typów.

- Sekcją thunk zarządzane do niezarządzanego jest wykonywany.

- Wywołania funkcji niezarządzanych (przy użyciu natywnych wersje argumenty).

- Thunk niezarządzane do zarządzanego jest wykonywany.

- Zwracany typ i dowolne "out" lub "w, out" argumenty są przekazywane z natywnego na typy CLR.

Sekcje Thunk zarządzanych/niezarządzanych są niezbędne dla współdziałania pracę na wszystkich, ale przekazywania danych, która jest wymagana zależy od typów danych związane, sygnatury funkcji i użycia danych.

Marshaling danych wykonywane przez międzyoperacyjności języka C++ jest to najprostsza forma możliwe: parametry są po prostu kopiowane przez granicę zarządzanych/niezarządzanych w sposób bitowe; Przekształcenie nie odbywa się w ogóle. Dla metody P/Invoke tylko jest to wartość true, jeśli wszystkie parametry są proste, typy danych kopiowalnych. W przeciwnym razie P/Invoke wykonuje stopniu niezawodną kroki, aby przekonwertować każdy parametr zarządzalny odpowiedni typ macierzysty i na odwrót, jeśli argumenty są oznaczone jako "out" lub "w, out".

Innymi słowy międzyoperacyjności języka C++ używa możliwe najszybszy sposób przekazywania danych, natomiast najbardziej niezawodna metoda korzysta z metody P/Invoke. Oznacza to, że domyślnie międzyoperacyjności języka C++ (w sposób typowe dla języka C++) zapewnia optymalną wydajność i potwierdzeniu programisty jest odpowiedzialny za adresowanie czasami to zachowanie nie jest bezpieczne lub nieodpowiednie.

Międzyoperacyjności języka C++ w związku z tym wymaga, że organizowanie danych musi być podana jawnie, ale zaletą jest to, że programisty jest bezpłatna dla zdecyduj, co jest potrzebne, biorąc pod uwagę rodzaj danych, jak ma być używany. Ponadto chociaż zachowanie marshalingu danych P/Invoke można modyfikować w dostosowane do pewnego stopnia, międzyoperacyjności języka C++ umożliwia danych skierowanie do można dostosować na podstawie wywołania przez wywołanie. Nie jest to możliwe przy użyciu metody P/Invoke.

Aby uzyskać więcej informacji na temat międzyoperacyjności języka C++, zobacz [za pomocą międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

## <a name="see-also"></a>Zobacz także

[Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)
