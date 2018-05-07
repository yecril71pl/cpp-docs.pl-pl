---
title: 'Porady: Definiowanie wyliczeń i korzystanie w języku C + +/ CLI | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enum class, specifying underlying types
ms.assetid: df8f2b91-b9d2-4fab-9be4-b1d58b8bc570
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f5c30b679b24e574d359a1f838785f0196f290d1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-and-consume-enums-in-ccli"></a>Porady: definiowanie wyliczeń w języku C++/interfejsie wiersza polecenia i korzystanie z nich
W tym temacie omówiono typy wyliczeniowe w języku C + +/ CLI.  
  
## <a name="specifying-the-underlying-type-of-an-enum"></a>Określanie typu podstawowego typu wyliczeniowego  
 Domyślnie jest podstawowy typ wyliczenia `int`.  Jednak można określić typ podpisem lub unsigned form `int`, `short`, `long`, `__int32`, lub `__int64`.  Można również użyć `char`.  
  
```  
// mcppv2_enum_3.cpp  
// compile with: /clr  
public enum class day_char : char {sun, mon, tue, wed, thu, fri, sat};  
  
int main() {  
   // fully qualified names, enumerator not injected into scope  
   day_char d = day_char::sun, e = day_char::mon;  
   System::Console::WriteLine(d);  
   char f = (char)d;  
   System::Console::WriteLine(f);  
   f = (char)e;  
   System::Console::WriteLine(f);  
   e = day_char::tue;  
   f = (char)e;  
   System::Console::WriteLine(f);  
}  
```  
  
 **Output**  
  
```Output  
sun  
0  
1  
2  
```  
  
## <a name="how-to-convert-between-managed-and-standard-enumerations"></a>Jak konwertować między wyliczeniami zarządzanymi a standardowymi  
 Nie jest konwersja standardowa między wyliczeniem i typem całkowitym; Rzutowanie jest wymagana.  
  
```  
// mcppv2_enum_4.cpp  
// compile with: /clr  
enum class day {sun, mon, tue, wed, thu, fri, sat};  
enum {sun, mon, tue, wed, thu, fri, sat} day2; // unnamed std enum  
  
int main() {  
   day a = day::sun;  
   day2 = sun;  
   if ((int)a == day2)  
   // or...  
   // if (a == (day)day2)  
      System::Console::WriteLine("a and day2 are the same");  
   else  
      System::Console::WriteLine("a and day2 are not the same");  
}  
```  
  
 **Output**  
  
```Output  
a and day2 are the same  
```  
  
## <a name="operators-and-enums"></a>Operatory i wyliczenia  
 Następujące operatory są prawidłowe dla wyliczeń w języku C + +/ CLI:  
  
|Operator|  
|--------------|  
|== != \< > \<= >=|  
|+ -|  
|&#124; ^ & ~|  
|++ --|  
|sizeof|  
  
 Operatory &#124; ^ & ~ ++ — są zdefiniowane tylko dla wyliczeń z podstawowych typów, z wyłączeniem bool całkowitych.  Obydwa argumenty operacji musi być typem wyliczenia.  
  
 Czy kompilator nie statyczne lub dynamiczne sprawdzenie wynik operacji wyliczenia. wartość nie jest w zakresie prawidłowy moduły wyliczające wyliczenia może spowodować operacji.  
  
> [!NOTE]
>  C ++ 11 wprowadza typy klas wyliczenia za pomocą kodu niezarządzanego, które różnią się od zarządzanych Wylicz klasy w języku C + +/ CLI. W szczególności typu klasy C ++ 11 wyliczenia nie obsługuje tej samej operatorów jako typ klasy zarządzanej wyliczenia w języku C + +/ CLI i C + +/ CLI kodu źródłowego musi dostarczyć specyfikator ułatwień dostępu w elemencie enum zarządzanych deklaracje klas aby odróżnić je od niezarządzane (C++ 11) deklaracje klas wyliczenia. Aby uzyskać więcej informacji na temat Wylicz klasy w języku C + +/ CLI, C + +/ CX i C ++ 11, zobacz [Wylicz klasy](../windows/enum-class-cpp-component-extensions.md).  
  
```  
// mcppv2_enum_5.cpp  
// compile with: /clr  
private enum class E { a, b } e, mask;  
int main() {  
   if ( e & mask )   // C2451 no E->bool conversion  
      ;  
  
   if ( ( e & mask ) != 0 )   // C3063 no operator!= (E, int)  
      ;  
  
   if ( ( e & mask ) != E() )   // OK  
      ;  
}  
```  
  
```  
// mcppv2_enum_6.cpp  
// compile with: /clr  
private enum class day : int {sun, mon};  
enum : bool {sun = true, mon = false} day2;  
  
int main() {  
   day a = day::sun, b = day::mon;  
   day2 = sun;  
  
   System::Console::WriteLine(sizeof(a));  
   System::Console::WriteLine(sizeof(day2));  
   a++;  
   System::Console::WriteLine(a == b);  
}  
```  
  
 **Output**  
  
```Output  
4  
1  
True  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Enum — klasa](../windows/enum-class-cpp-component-extensions.md)