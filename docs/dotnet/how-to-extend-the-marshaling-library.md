---
title: 'Porady: rozszerzanie biblioteki kierowania'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- Marshaling Library, extending
ms.assetid: 4c4a56d7-1d44-4118-b85f-f9686515e6e9
ms.openlocfilehash: 2a3dccd33b7ad2caee64e31e0f79180dda4649be
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216391"
---
# <a name="how-to-extend-the-marshaling-library"></a>Porady: rozszerzanie biblioteki kierowania

W tym temacie wyjaśniono, jak zwiększyć bibliotekę organizowania, aby zapewnić więcej konwersji między typami danych. Użytkownicy mogą rozszerać bibliotekę Marshal dla wszystkich konwersji danych, które nie są obecnie obsługiwane przez bibliotekę.

Bibliotekę Marshal można rozłożyć na dwa sposoby — z [klasą marshal_context](../dotnet/marshal-context-class.md)lub bez niej. Zapoznaj się z [omówieniem organizowania w temacie C++](../dotnet/overview-of-marshaling-in-cpp.md) , aby określić, czy nowa konwersja wymaga kontekstu.

W obu przypadkach należy najpierw utworzyć plik dla nowych konwersji do organizowania. Należy to zrobić, aby zachować integralność standardowych plików biblioteki do organizowania. Jeśli chcesz przenieść projekt na inny komputer lub do innego programisty, musisz skopiować nowy plik kierujący razem z resztą projektu. W ten sposób użytkownik otrzymujący projekt będzie zagwarantować otrzymywanie nowych konwersji i nie będzie musiał modyfikować żadnych plików biblioteki.

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-does-not-require-a-context"></a>Aby rozwinąć bibliotekę organizowania przy użyciu konwersji, która nie wymaga kontekstu

1. Utwórz plik do przechowywania nowych funkcji kierujących, na przykład Marshal. h.

1. Uwzględnij co najmniej jeden plik biblioteki Marshal:

   - Marshaling. h dla typów podstawowych.

   - marshal_windows. h dla typów danych systemu Windows.

   - marshal_cppstd. h dla typów danych standardowej biblioteki języka C++.

   - marshal_atl. h dla typów danych ATL.

1. Użyj kodu na końcu tych kroków, aby napisać funkcję konwersji. W tym kodzie, do jest typem do przekonwertowania na, z jest typem, z którego ma zostać wykonana konwersja, i `from` jest parametrem do przekonwertowania.

1. Zastąp komentarz dotyczący logiki konwersji z kodem, aby przekonwertować `from` parametr na obiekt typu i zwrócić przekonwertowany obiekt.

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

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-requires-a-context"></a>Aby rozwinąć bibliotekę organizowania z konwersją wymagającą kontekstu

1. Utwórz plik do przechowywania nowych funkcji kierujących, na przykład Marshal. h

1. Uwzględnij co najmniej jeden plik biblioteki Marshal:

   - Marshaling. h dla typów podstawowych.

   - marshal_windows. h dla typów danych systemu Windows.

   - marshal_cppstd. h dla typów danych standardowej biblioteki języka C++.

   - marshal_atl. h dla typów danych ATL.

1. Użyj kodu na końcu tych kroków, aby napisać funkcję konwersji. W tym kodzie, do jest typem do przekonwertowania na, z jest typem do przekonwertowania, `toObject` jest wskaźnikiem, w którym ma być przechowywany wynik, i `fromObject` jest parametrem do przekonwertowania.

1. Zastąp komentarz dotyczący inicjowania przy użyciu kodu, aby zainicjować `toPtr` do odpowiedniej pustej wartości. Na przykład, jeśli jest wskaźnikiem, ustaw go na wartość `NULL` .

1. Zastąp komentarz dotyczący logiki konwersji z kodem, aby przekonwertować `from` parametr na obiekt typu *do* . Ten przekonwertowany obiekt zostanie zapisany w `toPtr` .

1. Zamień komentarz dotyczący ustawienia na `toObject` kod, który ma zostać ustawiony `toObject` na przekonwertowany obiekt.

1. Zastąp komentarz dotyczący czyszczenia natywnych zasobów za pomocą kodu, aby zwolnić pamięć przydzieloną przez program `toPtr` . W przypadku `toPtr` przydzielenia pamięci za pomocą programu **`new`** Użyj polecenia, **`delete`** Aby zwolnić pamięć.

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

Poniższy przykład rozszerza bibliotekę organizowania z konwersją, która nie wymaga kontekstu. W tym przykładzie kod konwertuje informacje o pracowniku z typu danych natywnych na typ danych zarządzanych.

```cpp
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

W poprzednim przykładzie `marshal_as` Funkcja zwraca dojście do przekonwertowanych danych. Zostało to zrobione w celu uniemożliwienia tworzenia dodatkowej kopii danych. Zwrócenie zmiennej bezpośrednio spowodowałoby konieczność ponoszenia niepotrzebnego kosztu wydajności.

```Output
Managed name: Jeff Smith
Managed address: 123 Main Street
Managed zip code: 98111
```

## <a name="example"></a>Przykład

Poniższy przykład konwertuje informacje o pracownikach z zarządzanego typu danych na natywny typ danych. Ta konwersja wymaga kontekstu organizowania.

```cpp
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

[Omówienie organizowania w języku C++](../dotnet/overview-of-marshaling-in-cpp.md)
