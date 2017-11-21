---
title: "C4694 ostrzeżenia kompilatora | Dokumentacja firmy Microsoft"
ms.date: 10/25/2017
ms.technology: cpp-tools
ms.topic: article
f1_keywords: C4694
dev_langs: C++
helpviewer_keywords: C4694
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1af20859e394fe62403358107b74f9d1df5facb1
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="compiler-warning-c4694"></a>C4694 ostrzeżenia kompilatora

> "*klasy*": zapieczętowana klasa abstrakcyjna nie może mieć klasy podstawowej*base_class*"

Klasy abstrakcyjne i zapieczętowane nie może dziedziczyć z typu referencyjnego; Klasa zapieczętowany i abstrakcyjny nie można zaimplementować funkcje klasy podstawowej ani mógł służyć jako klasę podstawową.

Aby uzyskać więcej informacji, zobacz [abstrakcyjny](../../windows/abstract-cpp-component-extensions.md), [zapieczętowanego](../../windows/sealed-cpp-component-extensions.md), i [klas i struktur](../../windows/classes-and-structs-cpp-component-extensions.md).

To ostrzeżenie zostanie automatycznie podwyższony do wystąpił błąd. Jeśli chcesz zmienić to zachowanie, użyj [ostrzeżenie #pragma](../../preprocessor/warning.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C4694.

```cpp
// C4694.cpp
// compile with: /c /clr
ref struct A {};
ref struct B sealed abstract : A {};   // C4694
```