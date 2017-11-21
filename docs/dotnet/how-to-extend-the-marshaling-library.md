---
title: 'Porady: rozszerzanie biblioteki Marshalingu | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords: Marshaling Library, extending
ms.assetid: 4c4a56d7-1d44-4118-b85f-f9686515e6e9
caps.latest.revision: "27"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3133a8329dac0e20eeb5c3b3c8141e15a65aefe8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-extend-the-marshaling-library"></a>Porady: rozszerzanie biblioteki marshalingu
W tym temacie wyjaśniono, jak rozszerzanie biblioteki marshalingu, aby zapewnić więcej konwersje typów danych. Użytkownicy mogą rozszerzanie biblioteki marshalingu dla jakiejkolwiek konwersji danych nie jest obecnie obsługiwany przez bibliotekę.  
  
 Można rozszerzanie biblioteki marshalingu w jeden z dwóch sposobów - z lub bez [marshal_context — klasa](../dotnet/marshal-context-class.md). Przegląd [omówienie z Marshalingu w języku C++](../dotnet/overview-of-marshaling-in-cpp.md) tematu, aby określić, czy nowe konwersja wymaga kontekstu.  
  
 W obu przypadkach należy najpierw utworzyć pliku dla nowego kierowania konwersji. Możesz to zrobić w celu zachowania spójności standardowe przekazywanie plików biblioteki. Jeśli chcesz projekt do innego komputera lub programisty innego portu, należy skopiować nowy plik kierowania wraz z resztą projektu. W ten sposób użytkownika odbieranie projektu zostanie zapewniona do odbierania nowego konwersje i nie należy modyfikować pliki biblioteki.  
  
### <a name="to-extend-the-marshaling-library-with-a-conversion-that-does-not-require-a-context"></a>Aby rozszerzyć biblioteki organizowanie z konwersji, która nie wymaga kontekstu  
  
1.  Utwórz plik do przechowywania nowych funkcji kierowania, na przykład MyMarshal.h.  
  
2.  Zawierać co najmniej jeden z plików bibliotek kierowanie:  
  
    -   Marshal.h dla typów podstawowych.  
  
    -   marshal_windows.h dla typów danych systemu windows.  
  
    -   marshal_cppstd.h dla typów danych standardowa biblioteka C++.  
  
    -   marshal_atl.h dla typów danych ATL.  
  
3.  Użyj kodu po wykonaniu tych kroków można zapisać funkcji konwersji. W ten kod jest typ docelowy konwersji, FROM jest na typ docelowy konwersji z, a `from` jest parametrem, który ma zostać przekonwertowany.  
  
4.  Zamień na kod, aby przekonwertować komentarz dotyczący logiki konwersji `from` parametru w obiekt do typu i zwracać przekonwertowany obiekt.  
  
```  
namespace msclr {  
   namespace interop {  
      template<>  
      inline TO marshal_as<TO, FROM> (const FROM& from) {  
         // Insert conversion logic here, and return a TO parameter.  
      }  
   }  
}  
```  
  
### <a name="to-extend-the-marshaling-library-with-a-conversion-that-requires-a-context"></a>Aby rozszerzanie biblioteki Marshalingu z konwersji, która wymaga kontekstu  
  
1.  Utwórz plik do przechowywania nowych funkcji kierowania, na przykład MyMarshal.h  
  
2.  Zawierać co najmniej jeden z plików bibliotek kierowanie:  
  
    -   Marshal.h dla typów podstawowych.  
  
    -   marshal_windows.h dla typów danych systemu windows.  
  
    -   marshal_cppstd.h dla typów danych standardowa biblioteka C++.  
  
    -   marshal_atl.h dla typów danych ATL.  
  
3.  Użyj kodu po wykonaniu tych kroków można zapisać funkcji konwersji. W ten kod jest typ docelowy konwersji, FROM jest na typ docelowy konwersji, `toObject` wskaźnik do przechowywania wyników, a `fromObject` jest parametrem, który ma zostać przekonwertowany.  
  
4.  Zastąp komentarz dotyczący inicjowanie przy użyciu kod do zainicjowania `toPtr` na odpowiednią wartość pusta. Na przykład, jeśli jest wskaźnik, ustaw ją na `NULL`.  
  
5.  Zamień na kod, aby przekonwertować komentarz dotyczący logiki konwersji `from` parametru w obiekt *do* typu. Przekonwertowany obiekt będą przechowywane w `toPtr`.  
  
6.  Zastąp komentarz dotyczący ustawienie `toObject` z kodu, aby ustawić `toObject` obiektowi przekonwertowany.  
  
7.  Zastąp komentarz dotyczący czyszczenie zasobów natywnych z kodu, aby zwolnić wszystkie pamięci przydzielonej przez `toPtr`. Jeśli `toPtr` pamięci przydzielonej przy użyciu `new`, użyj `delete` można zwolnić pamięć.  
  
```  
namespace msclr {  
   namespace interop {  
      template<>  
      ref class context_node<TO, FROM> : public context_node_base  
      {  
      private:  
         TO toPtr;  
      public:  
         context_node(TO& toObject, FROM fromObject)  
         {  
            // (Step 4) Initialize toPtr to the appropriate empty value.  
            // (Step 5) Insert conversion logic here.  
            // (Step 6) Set toObject to the converted parameter.  
         }  
         ~context_node()  
         {  
            this->!context_node();  
         }  
      protected:  
         !context_node()  
         {  
            // (Step 7) Clean up native resources.  
         }  
      };  
   }  
}   
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rozszerza biblioteki marshalingu z konwersji, która nie wymaga kontekstu. W tym przykładzie kodu konwertuje informacje dotyczące pracowników z typem danych natywnych na typ danych zarządzanych.  
  
```  
// MyMarshalNoContext.cpp  
// compile with: /clr  
#include <msclr/marshal.h>  
  
value struct ManagedEmp {  
   System::String^ name;  
   System::String^ address;  
   int zipCode;  
};  
  
struct NativeEmp {  
   char* name;  
   char* address;  
   int zipCode;  
};  
  
namespace msclr {  
   namespace interop {  
      template<>  
      inline ManagedEmp^ marshal_as<ManagedEmp^, NativeEmp> (const NativeEmp& from) {  
         ManagedEmp^ toValue = gcnew ManagedEmp;  
         toValue->name = marshal_as<System::String^>(from.name);  
         toValue->address = marshal_as<System::String^>(from.address);  
         toValue->zipCode = from.zipCode;  
         return toValue;  
      }  
   }  
}  
  
using namespace System;  
using namespace msclr::interop;  
  
int main() {   
   NativeEmp employee;  
  
   employee.name = "Jeff Smith";  
   employee.address = "123 Main Street";  
   employee.zipCode = 98111;  
  
   ManagedEmp^ result = marshal_as<ManagedEmp^>(employee);  
  
   Console::WriteLine("Managed name: {0}", result->name);  
   Console::WriteLine("Managed address: {0}", result->address);  
   Console::WriteLine("Managed zip code: {0}", result->zipCode);  
  
   return 0;  
}  
```  
  
 W poprzednim przykładzie `marshal_as` funkcja zwraca uchwyt do przekonwertowanego danych. Było to, aby uniknąć tworzenia dodatkowych kopii danych. Zwracanie zmiennej bezpośrednio czy koszt wydajności niepotrzebnych skojarzony z go.  
  
```Output  
Managed name: Jeff Smith  
Managed address: 123 Main Street  
Managed zip code: 98111  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład konwertuje informacje dotyczące pracowników z typem danych zarządzanych na typ danych w trybie macierzystym. Ta konwersja wymaga kierowania kontekstu.  
  
```  
// MyMarshalContext.cpp  
// compile with: /clr  
#include <stdlib.h>  
#include <string.h>  
#include <msclr/marshal.h>  
  
value struct ManagedEmp {  
   System::String^ name;  
   System::String^ address;  
   int zipCode;  
};  
  
struct NativeEmp {  
   const char* name;  
   const char* address;  
   int zipCode;  
};  
  
namespace msclr {  
   namespace interop {  
      template<>  
      ref class context_node<NativeEmp*, ManagedEmp^> : public context_node_base  
      {  
      private:  
         NativeEmp* toPtr;  
         marshal_context context;  
      public:  
         context_node(NativeEmp*& toObject, ManagedEmp^ fromObject)  
         {  
            // Conversion logic starts here  
            toPtr = NULL;  
  
            const char* nativeName;  
            const char* nativeAddress;  
  
            // Convert the name from String^ to const char*.  
            System::String^ tempValue = fromObject->name;  
            nativeName = context.marshal_as<const char*>(tempValue);  
  
            // Convert the address from String^ to const char*.  
            tempValue = fromObject->address;  
            nativeAddress = context.marshal_as<const char*>(tempValue);  
  
            toPtr = new NativeEmp();  
            toPtr->name = nativeName;  
            toPtr->address = nativeAddress;  
            toPtr->zipCode = fromObject->zipCode;  
  
            toObject = toPtr;  
         }  
         ~context_node()  
         {  
            this->!context_node();  
         }  
      protected:  
         !context_node()  
         {  
            // When the context is deleted, it will free the memory  
            // allocated for toPtr->name and toPtr->address, so toPtr  
            // is the only memory that needs to be freed.  
            if (toPtr != NULL) {  
               delete toPtr;  
               toPtr = NULL;  
            }  
         }  
      };  
   }  
}   
  
using namespace System;  
using namespace msclr::interop;  
  
int main() {  
   ManagedEmp^ employee = gcnew ManagedEmp();  
  
   employee->name = gcnew String("Jeff Smith");  
   employee->address = gcnew String("123 Main Street");  
   employee->zipCode = 98111;  
  
   marshal_context context;  
   NativeEmp* result = context.marshal_as<NativeEmp*>(employee);  
  
   if (result != NULL) {  
      printf_s("Native name: %s\nNative address: %s\nNative zip code: %d\n",  
         result->name, result->address, result->zipCode);  
   }  
  
   return 0;  
}  
```  
  
```Output  
Native name: Jeff Smith  
Native address: 123 Main Street  
Native zip code: 98111  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie Marshalingu w języku C++](../dotnet/overview-of-marshaling-in-cpp.md)