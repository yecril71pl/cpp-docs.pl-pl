---
title: "Statyczne elementy członkowskie (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0d19985271648e66aa86946c685608f805b1dfe1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="static-members-c"></a>Statyczne elementy członkowskie (C++)
Klasy może zawierać danych statycznych elementów członkowskich i funkcji elementów członkowskich. Gdy element danych jest zadeklarowany jako **statycznych**, tylko jedną kopię danych jest obsługiwane dla wszystkich obiektów klasy.
  
 Statyczne elementy członkowskie danych nie są częścią obiektów typu danej klasy. W związku z tym deklaracji elementu członkowskiego danych statycznych nie jest uważana za definicji. Element członkowski danych jest zadeklarowany w zakresie klasy, ale definicji odbywa się w zakresie pliku. Te statycznych elementów członkowskich mają połączenie zewnętrzne. Poniższy przykład przedstawia to:  
  
```  
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
  
 W powyższym kodzie, element członkowski `bytecount` jest zadeklarowana w klasie `BufferedOutput`, ale musi być zdefiniowana poza deklaracją klasy.  
  
 Statyczne elementy członkowskie danych mogą być przywoływane bez odwołujących się do obiektu typu klasy. Liczba bajtów zapisanych przy użyciu `BufferedOutput` obiektów można uzyskać w następujący sposób:  
  
```  
long nBytes = BufferedOutput::bytecount;  
```  
  
 Statyczny element członkowski istnieje nie jest konieczne, że istnieją wszystkie obiekty typu klasy. Statyczne elementy Członkowskie mogą również dostęp za pomocą wyboru elementu członkowskiego (**.** i  **->** ) operatorów. Na przykład:  
  
```  
BufferedOutput Console;  
  
long nBytes = Console.bytecount;  
```  
  
 W przypadku poprzedniego odwołania do obiektu (`Console`) nie jest oceniany; wartość zwracana jest statyczny obiekt `bytecount`.  
  
 Statyczne elementy członkowskie danych podlegają reguły dostępu do elementu członkowskiego klasy, więc prywatny dostęp do danych statycznych elementów członkowskich jest dozwolony tylko w przypadku funkcji elementów członkowskich klasy i znajomych. Te reguły są opisane w [kontroli dostępu do elementu członkowskiego](../cpp/member-access-control-cpp.md). Wyjątkiem są przez elementy członkowskie muszą być zdefiniowane w zakresie pliku niezależnie od ich ograniczenia dostępu do danych statycznych. Jeśli element członkowski danych jest jawnie zostać zainicjowana, należy podać z definicją inicjatora.  
  
 Typ statyczny element członkowski nie jest kwalifikowany za pomocą nazwy klasy. W związku z tym typem `BufferedOutput::bytecount` jest `long`.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy i struktury](../cpp/classes-and-structs-cpp.md)