---
title: Współdziałanie z innymi językami .NET (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++, indexers
- indexers, consuming C#
- as C# keyword [C++]
- is C# keyword [C++]
- lock statement
- lock C# keyword [C++]
ms.assetid: a5902cf8-a14d-4559-aefb-c178615d45bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 000009eca8150774150ab1e1d8f6d228aaf5c912
ms.sourcegitcommit: 27be37ae07ee7b657a54d23ed34438220d977fdc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/18/2018
ms.locfileid: "39110302"
---
# <a name="interoperability-with-other-net-languages-ccli"></a>Współdziałanie z innymi językami .NET (C++/CLI)
Tematy w tej sekcji przedstawiają sposób tworzenia zestawów w programie Visual C++, które używają z lub zapewniać funkcje w zestawach napisanych w języku C# lub Visual Basic.  
  
## <a name="consume_indexer"></a> Konsumowanie indeksatora języka C#
Visual C++ nie zawiera indeksatory; ma ona właściwości indeksowanych. Aby konsumowanie indeksatora języka C#, uzyskać dostęp do indeksatora, tak jakby indeksowana właściwość.  
  
 Aby uzyskać więcej informacji na temat indeksatorów zobacz:  
  
-   [Indeksatory](/dotnet/csharp/programming-guide/indexers/index)  
  
### <a name="example"></a>Przykład  
 Następujący program C# definiuje indeksatora.  
  
```csharp  
// consume_cs_indexers.cs  
// compile with: /target:library  
using System;  
public class IndexerClass {  
   private int [] myArray = new int[100];   
   public int this [int index] {   // Indexer declaration  
      get {  
         // Check the index limits.  
         if (index < 0 || index >= 100)  
            return 0;  
         else  
            return myArray[index];  
      }  
      set {  
         if (!(index < 0 || index >= 100))  
            myArray[index] = value;  
      }  
   }  
}  
/*  
// code to consume the indexer  
public class MainClass {  
   public static void Main() {  
      IndexerClass b = new IndexerClass();  
  
      // Call indexer to initialize elements 3 and 5  
      b[3] = 256;  
      b[5] = 1024;  
      for (int i = 0 ; i <= 10 ; i++)   
         Console.WriteLine("Element #{0} = {1}", i, b[i]);  
   }  
}  
*/  
```  
  
### <a name="example"></a>Przykład  
 Indeksator korzysta z tego programu Visual C++.  
  
```cpp  
// consume_cs_indexers_2.cpp  
// compile with: /clr  
#using "consume_cs_indexers.dll"  
using namespace System;  
  
int main() {  
   IndexerClass ^ ic = gcnew IndexerClass;  
   ic->default[0] = 21;  
   for (int i = 0 ; i <= 10 ; i++)  
      Console::WriteLine("Element #{0} = {1}", i, ic->default[i]);  
}  
```  
  
```Output  
Element #0 = 21  
Element #1 = 0  
Element #2 = 0  
Element #3 = 0  
Element #4 = 0  
Element #5 = 0  
Element #6 = 0  
Element #7 = 0  
Element #8 = 0  
Element #9 = 0  
Element #10 = 0  
```  

## <a name="implement_isas"></a> Implementowanie jest i jak słowa kluczowe języka C#
W tym temacie pokazano, jak zaimplementować funkcje `is` i `as` słowa kluczowe języka C# w programie Visual C++.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// CS_is_as.cpp  
// compile with: /clr  
using namespace System;  
  
interface class I {  
public:  
   void F();  
};  
  
ref struct C : public I {  
   virtual void F( void ) { }  
};  
  
template < class T, class U >   
Boolean isinst(U u) {  
   return dynamic_cast< T >(u) != nullptr;  
}  
  
int main() {  
   C ^ c = gcnew C();  
   I ^ i = safe_cast< I ^ >(c);   // is (maps to castclass in IL)  
   I ^ ii = dynamic_cast< I ^ >(c);   // as (maps to isinst in IL)  
  
   // simulate 'as':  
   Object ^ o = "f";  
   if ( isinst< String ^ >(o) )  
      Console::WriteLine("o is a string");  
}  
```  
  
```Output  
o is a string  
```  

## <a name="implement_locak"></a> Implementowanie słowa kluczowego lock języka C#
W tym temacie przedstawiono sposób implementacji języka C# `lock` — słowo kluczowe w języku Visual C++. 
  
 Można również użyć `lock` klasy w języku C++ Support Library. Zobacz [synchronizacja (klasa lock)](../dotnet/synchronization-lock-class.md) Aby uzyskać więcej informacji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// CS_lock_in_CPP.cpp  
// compile with: /clr  
using namespace System::Threading;  
ref class Lock {  
   Object^ m_pObject;  
public:  
   Lock( Object ^ pObject ) : m_pObject( pObject ) {  
      Monitor::Enter( m_pObject );  
   }  
   ~Lock() {  
      Monitor::Exit( m_pObject );  
   }  
};  
  
ref struct LockHelper {  
   void DoSomething();  
};  
  
void LockHelper::DoSomething() {  
   // Note: Reference type with stack allocation semantics to provide   
   // deterministic finalization  
  
   Lock lock( this );     
   // LockHelper instance is locked  
}  
  
int main()  
{  
   LockHelper lockHelper;  
   lockHelper.DoSomething();  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
