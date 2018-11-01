---
title: Kompilator ostrzeżenie (poziom 1) C4376
ms.date: 11/04/2016
f1_keywords:
- C4376
helpviewer_keywords:
- C4376
ms.assetid: 5f202c74-9489-48fe-b36f-19cd882b1589
ms.openlocfilehash: b1f6e7b403931f7fe1a67974ae85001cf80eab66
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451600"
---
# <a name="compiler-warning-level-1-c4376"></a>Kompilator ostrzeżenie (poziom 1) C4376

Specyfikator dostępu "old_specifier:" nie jest już obsługiwany: Użyj "new_specifier:" zamiast niego

Aby uzyskać więcej informacji na temat określania dostępność typów i elementów członkowskich w metadanych, zobacz [typ widoczności](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) i [widoczności składowych](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility) w [porady: definiowanie i Consume Classes and Structs (C + +/ interfejsu wiersza polecenia) ](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4376.

```
// C4376.cpp
// compile with: /clr /W1 /c
public ref class G {
public public:   // C4376
   void m2();
};

public ref class H {
public:   // OK
   void m2();
};
```