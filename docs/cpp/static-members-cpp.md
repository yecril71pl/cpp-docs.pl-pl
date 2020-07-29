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
ms.openlocfilehash: b79b65ab3cbf4565f31ad6717f8163c678697c9c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213193"
---
# <a name="static-members-c"></a>Statyczne elementy członkowskie (C++)

Klasy mogą zawierać statyczne dane elementów członkowskich i funkcje członkowskie. Gdy element członkowski danych jest zadeklarowany jako **`static`** , tylko jedna kopia danych jest utrzymywana dla wszystkich obiektów klasy.

Statyczne elementy członkowskie danych nie są częścią obiektów danego typu klasy. W związku z tym deklaracja statycznego elementu członkowskiego danych nie jest uważana za definicję. Element członkowski danych jest zadeklarowany w zakresie klasy, ale definicja jest wykonywana w zakresie pliku. Te statyczne elementy członkowskie mają powiązania zewnętrzne. Zostało to przedstawione w poniższym przykładzie:

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

W poprzednim kodzie element członkowski `bytecount` jest zadeklarowany w klasie `BufferedOutput` , ale musi być zdefiniowany poza deklaracją klasy.

Statyczne składowe danych mogą być określane bez odwoływania się do obiektu typu klasy. Liczba bajtów zapisanych przy użyciu `BufferedOutput` obiektów można uzyskać w następujący sposób:

```cpp
long nBytes = BufferedOutput::bytecount;
```

Aby statyczny element członkowski mógł istnieć, nie jest konieczne, aby istniały wszystkie obiekty typu klasy. Dostęp do statycznych elementów członkowskich można także uzyskać za pomocą wyboru elementu członkowskiego (**.** and **->** ). Na przykład:

```cpp
BufferedOutput Console;

long nBytes = Console.bytecount;
```

W poprzednim przypadku odwołanie do obiektu ( `Console` ) nie jest oceniane; zwrócona wartość jest równa obiektowi statycznemu `bytecount` .

Statyczne elementy członkowskie danych podlegają regułom dostępu do elementów członkowskich klasy, więc prywatny dostęp do statycznych elementów członkowskich danych jest dozwolony tylko dla funkcji składowych i znajomych klasy. Te reguły są opisane w [Access Control elementu członkowskiego](../cpp/member-access-control-cpp.md). Wyjątek polega na tym, że statyczne elementy członkowskie danych muszą być zdefiniowane w zakresie pliku, niezależnie od ich ograniczeń dostępu. Jeśli składowa danych ma być jawnie inicjowana, inicjator musi być dostarczony z definicją.

Typ statycznego elementu członkowskiego nie kwalifikuje się do jego nazwy klasy. W związku z tym typem `BufferedOutput::bytecount` jest **`long`** .

## <a name="see-also"></a>Zobacz także

[Klasy i struktury](../cpp/classes-and-structs-cpp.md)
