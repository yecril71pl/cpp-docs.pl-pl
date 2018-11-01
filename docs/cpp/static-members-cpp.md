---
title: Statyczne elementy członkowskie (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- class members [C++], static
- instance constructors, static members
- class members [C++], shared
- members [C++], static data members
- static members [C++], data members
- static data members [C++]
- data members [C++], static data members
- class instances [C++], shared members
- instance constructors, shared members
- class instances [C++], static members
ms.assetid: 9cc8cf0f-d74c-46f2-8e83-42d4e42c8370
ms.openlocfilehash: 708f78c09db263584d478d16863999d4428e4891
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635256"
---
# <a name="static-members-c"></a>Statyczne elementy członkowskie (C++)

Klasy mogą zawierać statyczny element członkowski danych i elementów członkowskich. Gdy element członkowski danych jest zadeklarowany jako **statyczne**, tylko jedna kopia danych jest zachowywana na potrzeby wszystkich obiektów klasy.

Statyczne elementy członkowskie danych nie są częścią obiektów typu danej klasy. W rezultacie deklaracja składowej danych statycznych nie jest uważany za definicję. Element członkowski danych jest zadeklarowana w zakresie klasy, ale definicji odbywa się w zakresie pliku. Te statyczne elementy członkowskie mają powiązania zewnętrzne. Ilustruje to poniższy przykład:

```cpp
// static_data_members.cpp
class BufferedOutput
{
public:
   // Return number of bytes written by any object of this class.
   short BytesWritten()
   {
      return bytecount;
   }

   // Reset the counter.
   static void ResetCount()
   {
      bytecount = 0;
   }

   // Static member declaration.
   static long bytecount;
};

// Define bytecount in file scope.
long BufferedOutput::bytecount;

int main()
{
}
```

W poprzednim kodzie elementu członkowskiego `bytecount` jest zadeklarowana w klasie `BufferedOutput`, ale musi być zdefiniowana poza deklaracją klasy.

Statyczne elementy członkowskie danych można się odwoływać bez odwołujące się do obiektu typu klasy. Liczba bajtów zapisanych, za pomocą `BufferedOutput` obiektów można uzyskać w następujący sposób:

```cpp
long nBytes = BufferedOutput::bytecount;
```

Statyczny element członkowski ma nie jest to konieczne, że istnieją wszystkie obiekty typu klasy. Statyczne elementy członkowskie można również uzyskać dostęp za pomocą wyboru elementów członkowskich (**.** i **->**) operatorów. Na przykład:

```cpp
BufferedOutput Console;

long nBytes = Console.bytecount;
```

W przypadku poprzedniego odwołanie do obiektu (`Console`) nie jest oceniany; wartość zwracana jest to, że obiektu statycznego `bytecount`.

Statyczne elementy członkowskie danych podlegają reguły dostępu do składowej klasy, więc prywatny dostęp do elementów członkowskich danych statycznych jest dozwolony tylko w przypadku funkcji składowych klasy i znajomym. Te reguły są opisane w [kontroli dostępu do elementu członkowskiego](../cpp/member-access-control-cpp.md). Wyjątek stanowi tego dane statyczne, które elementy członkowskie muszą być zdefiniowane w zakresie pliku, niezależnie od ich ograniczenia dostępu. Jeśli składowej danych, które ma być jawnie zainicjowana, należy podać inicjatora z definicją.

Typ członka statycznego nie jest kwalifikowana przez nazwę klasy. W związku z tym, typ `BufferedOutput::bytecount` jest **długie**.

## <a name="see-also"></a>Zobacz także

[Klasy i struktury](../cpp/classes-and-structs-cpp.md)