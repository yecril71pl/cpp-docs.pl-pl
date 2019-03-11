---
title: 'Instrukcje: Rozszerzanie biblioteki Marshalingu'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- Marshaling Library, extending
ms.assetid: 4c4a56d7-1d44-4118-b85f-f9686515e6e9
ms.openlocfilehash: f289539807b1e9499cef51427d3f6a494545cc60
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750366"
---
# <a name="how-to-extend-the-marshaling-library"></a>Instrukcje: Rozszerzanie biblioteki Marshalingu

W tym temacie wyjaśniono, jak rozszerzanie biblioteki marshalingu, aby zapewnić więcej konwersje między typami danych. Użytkownicy mogą rozszerzanie biblioteki marshalingu podczas konwersji wszelkie dane, nie są obecnie obsługiwane przez bibliotekę.

Możesz rozszerzyć Biblioteka dotycząca organizowania w jeden z dwóch sposobów - z lub bez [marshal_context Class](../dotnet/marshal-context-class.md). Przegląd [Overview of Marshaling w C++](../dotnet/overview-of-marshaling-in-cpp.md) tematu, aby określić, czy nowe konwersja wymaga kontekstu.

W obu przypadkach należy najpierw utworzyć plik dla nowych konwersji organizowania. Możesz to zrobić w celu zachowania spójności standardowe szeregowanie pliki biblioteki. Jeśli chcesz przenieść projektu do innego komputera lub do innego programisty, należy skopiować nowy plik organizowania wraz z resztą projektu. W ten sposób otrzymania projektu przez użytkownika będą miały zagwarantowane, aby otrzymać nowy konwersji i nie trzeba modyfikować dowolnych plikach bibliotek.

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-does-not-require-a-context"></a>Aby rozszerzyć Marshaling biblioteki za pomocą konwersji, która nie wymaga kontekstu

1. Utwórz plik do przechowywania z nowych funkcji organizowania, na przykład MyMarshal.h.

1. Obejmują jeden lub więcej plików biblioteki marshal:

   - Marshal.h dla typów podstawowych.

   - marshal_windows.h dla typów danych systemu windows.

   - marshal_cppstd.h dla typów danych standardowej biblioteki języka C++.

   - marshal_atl.h ATL typów danych.

1. Użyj kodu po wykonaniu tych kroków, aby zapisać funkcji konwersji. W tym kodzie jest typ docelowy konwersji, FROM na typ docelowy konwersji, a `from` jest parametr, który ma zostać przekonwertowany.

1. Zamień na kod konwertujący komentarz dotyczący logiki konwersji `from` parametru w obiekt na typ i zwraca obiekt przekonwertowany.

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

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-requires-a-context"></a>Aby rozszerzyć Biblioteka dotycząca organizowania za pomocą konwersji, która wymaga kontekstu

1. Utwórz plik do przechowywania z nowych funkcji organizowania, na przykład MyMarshal.h

1. Obejmują jeden lub więcej plików biblioteki marshal:

   - Marshal.h dla typów podstawowych.

   - marshal_windows.h dla typów danych systemu windows.

   - marshal_cppstd.h dla typów danych standardowej biblioteki języka C++.

   - marshal_atl.h ATL typów danych.

1. Użyj kodu po wykonaniu tych kroków, aby zapisać funkcji konwersji. W tym kodzie jest typ docelowy konwersji, FROM na typ docelowy konwersji, `toObject` jest wskaźnikiem do przechowywania wyników, a `fromObject` jest parametr, który ma zostać przekonwertowany.

1. Zastąp komentarz dotyczący inicjowanie przy użyciu kodu w celu zainicjowania `toPtr` odpowiednią wartość pusta. Na przykład, jeśli jest to wskaźnik, ustaw ją na `NULL`.

1. Zamień na kod konwertujący komentarz dotyczący logiki konwersji `from` parametru w obiekt *na* typu. Ten obiekt przekonwertowany będą przechowywane w `toPtr`.

1. Zastąp komentarz dotyczący ustawienie `toObject` kodem, aby ustawić `toObject` obiektowi przekonwertowana.

1. Zastąp komentarzy dotyczących usuwania zasobów natywnych z kodu, aby zwolnić wszystkie pamięci przydzielonej przez `toPtr`. Jeśli `toPtr` przydzieloną pamięć przy użyciu `new`, użyj `delete` zwolnienie pamięci.

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

Poniższy przykład rozszerza Biblioteka dotycząca organizowania za pomocą konwersji, która nie wymaga kontekstu. W tym przykładzie kodu konwertuje informacje dotyczące pracowników z typem danych natywnych z typem danych zarządzanych.

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

W poprzednim przykładzie `marshal_as` funkcja zwraca uchwyt do przekonwertowanego danych. Zostało to zrobione, aby uniknąć tworzenia dodatkowych kopię danych. Bezpośrednio przekazujących zmiennej może być spadek wydajności niepotrzebne skojarzony z.

```Output
Managed name: Jeff Smith
Managed address: 123 Main Street
Managed zip code: 98111
```

## <a name="example"></a>Przykład

Poniższy przykład konwertuje informacje dotyczące pracowników z typem danych zarządzanych z typem danych natywnych. Ta konwersja wymaga organizowania kontekstu.

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

## <a name="see-also"></a>Zobacz także

[Omówienie marshalingu w języku C++](../dotnet/overview-of-marshaling-in-cpp.md)
