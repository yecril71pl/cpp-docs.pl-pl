---
title: Przeciążone operatory | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- operator overloading, in a CLR class
- operators [C++], overloading
ms.assetid: 30391426-afe7-4497-bf22-e4816c1e48c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a53b8df6f10a4fb8efcd91ce5d9c3f0125320139
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425863"
---
# <a name="overloaded-operators"></a>Operatory przeciążone

Przeciążanie operatora zmienił się znacznie z zarządzanych rozszerzeń dla języka C++ do Visual C++.

W deklaracji typu odwołania, aby uzyskać przykład, zamiast korzystać z natywnych `operator+` składni, możesz jawnie zapisać wewnętrzna nazwa podstawowej operatora — w tym przypadku `op_Addition`. Ponadto wywołanie operatora musi być jawnie wywoływane za pośrednictwem tej samej nazwie, w związku z tym ograniczenia dwie podstawowe korzyści przeciążenia operatora: (składni intuicyjne i (b) możliwość intermix nowych typów z istniejących typów. Na przykład:

```
public __gc __sealed class Vector {
public:
   Vector( double x, double y, double z );

   static bool    op_Equality( const Vector*, const Vector* );
   static Vector* op_Division( const Vector*, double );
   static Vector* op_Addition( const Vector*, const Vector* );
   static Vector* op_Subtraction( const Vector*, const Vector* );
};

int main()
{
   Vector *pa = new Vector( 0.231, 2.4745, 0.023 );
   Vector *pb = new Vector( 1.475, 4.8916, -1.23 );

   Vector *pc1 = Vector::op_Addition( pa, pb );
   Vector *pc2 = Vector::op_Subtraction( pa, pc1 );
   Vector *pc3 = Vector::op_Division( pc1, pc2->x );

   if ( Vector::op_Equality( pc1, pc2 ))
      ;
}
```

W nowej składni są przywracane zwykle oczekiwania programistą natywnego języka C++, zarówno w deklaracji i użyj statycznych operatorów. Oto `Vector` klasy przetłumaczyć nowej składni:

```
public ref class Vector sealed {
public:
   Vector( double x, double y, double z );

   static bool    operator ==( const Vector^, const Vector^ );
   static Vector^ operator /( const Vector^, double );
   static Vector^ operator +( const Vector^, const Vector^ );
   static Vector^ operator -( const Vector^, const Vector^ );
};

int main()
{
   Vector^ pa = gcnew Vector( 0.231, 2.4745, 0.023 );
   Vector^ pb = gcnew Vector( 1.475,4.8916,-1.23 );

   Vector^ pc1 = pa + pb;
   Vector^ pc2 = pa - pc1;
   Vector^ pc3 = pc1 / pc2->x;

   if ( pc1 == pc2 )
      ;
}
```

## <a name="see-also"></a>Zobacz też

[Deklaracje składowych w obrębie klasy lub interfejsu (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)