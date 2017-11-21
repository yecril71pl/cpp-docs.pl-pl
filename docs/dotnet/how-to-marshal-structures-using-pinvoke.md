---
title: "Porady: kierowanie struktur za pomocą funkcji PInvoke | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- data marshaling [C++], structures
- platform invoke [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: 35997e6f-9251-4af3-8c6e-0712d64d6a5d
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 52fa9aece3f31cf20029e58352d459f91bb56526
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-marshal-structures-using-pinvoke"></a>Porady: przeprowadzanie marshalingu struktur za pomocą funkcji PInvoke
W tym dokumencie opisano sposób natywny funkcje, których można wywołać ciągów w stylu języka C z zarządzanego funkcji, które zapewniają wystąpienia <xref:System.String> przy użyciu metody P/Invoke. Mimo że zalecane jest użycie funkcji międzyoperacyjności języka C++, zamiast P/Invoke ponieważ P/Invoke zapewnia małego błąd kompilacji raportowania, nie jest bezpieczne i może być niewygodne wdrożenia, jeśli niezarządzanego API jest dostarczana jako biblioteki DLL i kod źródłowy jest dostępne, P/Invoke jest jedyną opcją. W przeciwnym razie można znaleźć w następujących dokumentach:  
  
-   [Za pomocą międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
-   [Porady: kierowanie struktur za pomocą funkcji PInvoke](../dotnet/how-to-marshal-structures-using-pinvoke.md)  
  
 Domyślnie struktury natywnych i zarządzanych są wyświetlane inaczej w pamięci, dlatego pomyślnie przekazywanie struktur granicy zarządzanych/niezarządzanych wymaga dodatkowych czynności w celu zachowania integralności danych.  
  
 W tym dokumencie opisano kroki wymagane do zdefiniowania zarządzanych odpowiedników natywnego struktur i jak wynikowy struktury mogą zostać przekazane z funkcjami niezarządzanymi. Ten dokument przy założeniu, że proste struktury — te, które nie zawierają ciągi lub wskaźniki — są używane. Aby uzyskać informacje o współdziałaniu niekopiowalne, zobacz [za pomocą międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md). P/Invoke nie może mieć niekopiowalne jako do wartości zwracanej. Typy Kopiowalne ma taką samą reprezentację w kodzie zarządzane i niezarządzane. Aby uzyskać więcej informacji, zobacz [Kopiowalne i typy Kopiowalne inne niż](http://msdn.microsoft.com/Library/d03b050e-2916-49a0-99ba-f19316e5c1b3).  
  
 Organizowanie proste, struktur danych kopiowalnych granicy zarządzanych/niezarządzanych najpierw wymaga zdefiniowania zarządzanych wersje każdego natywnego struktury. Te struktury może mieć dowolną nazwę prawne; nie ma żadnej zależności między wersjami natywnych i zarządzanych dwie struktury niż ich układ danych. W związku z tym jest niezbędne, aby zarządzanej wersji zawiera pola, które są takie same, rozmiar i w tej samej kolejności jak natywną wersję. (Nie istnieje mechanizm dla zapewniające zarządzanego i natywnego wersji struktury, więc niezgodności nie staną się widoczne do czasu wykonywania. Jest odpowiedzialny za programisty, aby upewnić się, że dwie struktury mają ten sam układ danych).  
  
 Ponieważ członków struktur zarządzane są czasami przestawiać względów wydajności, jest konieczne użycie <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutu, aby wskazać, że struktura układ sekwencyjnie. Jest również dobrym pomysłem jest jawnie ustawiona struktura pakowania ustawienie, aby być taka sama jak używany przez natywnego struktury. (Mimo że domyślnie Visual C++ używa struktury 8-bajtowych pakowania zarówno kod zarządzany).  
  
1.  Następnie użyj <xref:System.Runtime.InteropServices.DllImportAttribute> zadeklarować punktów wejścia, które odpowiadają niezarządzane funkcje, które akceptują strukturę, ale zarządzanej wersji struktury w sygnatury funkcji, który jest punktem moot, korzystając z tej samej nazwy dla obie wersje Struktura.  
  
2.  Teraz kod zarządzany można przekazać zarządzanej wersji struktury z funkcjami niezarządzanymi tak, jakby są faktycznie zarządzanego funkcji. Te struktury mogą być przekazywane przez wartość lub przez odwołanie, jak pokazano w poniższym przykładzie.  
  
## <a name="example"></a>Przykład  
 Poniższy kod składa się z modułu zarządzanych i niezarządzanych. Moduł niezarządzanym jest bibliotekę DLL, która definiuje strukturę o nazwie lokalizacji i funkcji o nazwie GetDistance, który akceptuje dwa wystąpienia struktury lokalizacji. Drugi moduł jest aplikacją wiersza polecenia zarządzanych, importuje funkcja GetDistance, ale definiuje ją pod względem odpowiednika zarządzanych konstrukcji lokalizacji MLocation. W praktyce tej samej nazwie będzie prawdopodobnie używany na potrzeby obie wersje konstrukcji; jednak różnych nazwa jest używana w tym miejscu wykazać, że prototypu DllImport jest zdefiniowany w zarządzanej wersji.  
  
 Moduł zarządzany została skompilowana z/CLR, ale/CLR: pure działa również. **/CLR: pure** i **/CLR: Safe** — opcje kompilatora zostały uznane za przestarzałe w programie Visual Studio 2015.  
  
 Należy pamiętać, że żadna jego część biblioteki DLL jest narażony na kod zarządzany przy użyciu tradycyjnych # dyrektywy include. W rzeczywistości plik DLL, który jest dostępny tylko w czasie wykonywania, problemy z funkcjami zaimportowane z DllImport nie zostanie wykryty w czasie kompilacji.  
  
```  
// TraditionalDll3.cpp  
// compile with: /LD /EHsc  
#include <iostream>  
#include <stdio.h>  
#include <math.h>  
  
#define TRADITIONALDLL_EXPORTS  
#ifdef TRADITIONALDLL_EXPORTS  
   #define TRADITIONALDLL_API __declspec(dllexport)  
#else  
   #define TRADITIONALDLL_API __declspec(dllimport)  
#endif  
  
#pragma pack(push, 8)  
struct Location {  
   int x;  
   int y;  
};  
#pragma pack(pop)  
  
extern "C" {  
   TRADITIONALDLL_API double GetDistance(Location, Location);  
   TRADITIONALDLL_API void InitLocation(Location*);  
}  
  
double GetDistance(Location loc1, Location loc2) {  
   printf_s("[unmanaged] loc1(%d,%d)", loc1.x, loc1.y);  
   printf_s(" loc2(%d,%d)\n", loc2.x, loc2.y);  
  
   double h = loc1.x - loc2.x;  
   double v = loc1.y = loc2.y;  
   double dist = sqrt( pow(h,2) + pow(v,2) );  
  
   return dist;  
}  
  
void InitLocation(Location* lp) {  
   printf_s("[unmanaged] Initializing location...\n");  
   lp->x = 50;  
   lp->y = 50;  
}  
```  
  
## <a name="example"></a>Przykład  
  
```  
// MarshalStruct_pi.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
[StructLayout(LayoutKind::Sequential, Pack=8)]  
value struct MLocation {  
   int x;  
   int y;  
};  
  
value struct TraditionalDLL {  
   [DllImport("TraditionalDLL3.dll")]  
   static public double GetDistance(MLocation, MLocation);  
   [DllImport("TraditionalDLL3.dll")]  
   static public double InitLocation(MLocation*);  
};  
  
int main() {  
   MLocation loc1;  
   loc1.x = 0;  
   loc1.y = 0;  
  
   MLocation loc2;  
   loc2.x = 100;  
   loc2.y = 100;  
  
   double dist = TraditionalDLL::GetDistance(loc1, loc2);  
   Console::WriteLine("[managed] distance = {0}", dist);  
  
   MLocation loc3;  
   TraditionalDLL::InitLocation(&loc3);  
   Console::WriteLine("[managed] x={0} y={1}", loc3.x, loc3.y);  
}  
```  
  
```Output  
[unmanaged] loc1(0,0) loc2(100,100)  
[managed] distance = 141.42135623731  
[unmanaged] Initializing location...  
[managed] x=50 y=50  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)