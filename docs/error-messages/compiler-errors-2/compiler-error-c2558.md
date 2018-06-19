---
title: C2558 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2558
dev_langs:
- C++
helpviewer_keywords:
- C2558
ms.assetid: 822b701e-dcae-423a-b21f-47f36aff9c90
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7db417edebf0a1fff6ef87bf8ae407889a0e0af
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33231865"
---
# <a name="compiler-error-c2558"></a>C2558 błąd kompilatora
'identifier' : nie ma dostępnego konstruktora kopiującego lub konstruktor kopiujący jest zadeklarowany jako 'explicit'  
  
 Konstruktor kopiujący inicjuje obiekt z innego obiektu tego samego typu. (Tworzy kopię obiektu.) Kompilator generuje domyślny konstruktor kopiujący, jeżeli nie zdefiniujesz żadnych konstruktorów.  
  
### <a name="to-fix-this-error"></a>Aby naprawić ten błąd  
  
1.  Ten problem może wystąpić, gdy podejmowana jest próba, aby skopiować klasy, w których Konstruktor kopiujący jest `private`. W większości przypadków klasy, która ma `private` Konstruktor kopiujący nie powinny być kopiowane. Deklaruje typowe techniki programowania `private` konstruktora kopiującego, aby zapobiec bezpośredniego użycia klasy. Klasa może być bezużyteczna samodzielnie lub wymagać innej klasy, aby działać poprawnie.  
  
     Jeśli okaże się, że jest bezpiecznie korzystać klasy, która ma `private` Konstruktor kopiujący, pochodzi z klasy, która ma nową klasę `private` Konstruktor i udostępnić `public` lub `protected` Konstruktor kopiujący jest dostępne w nowej klasy. Użyj klasy pochodnej zamiast oryginalnej.  
  
2.  Ten problem może wystąpić, gdy podejmowana jest próba, aby skopiować klasy, w których Konstruktor kopiujący jest jawne. Deklarowanie konstruktora kopiującego jako `explicit` uniemożliwia przekazywanie/zwracanie obiektów klasy do/z funkcji. Aby uzyskać więcej informacji na temat jawnych konstruktorów, zobacz [zdefiniowane przez użytkownika konwersje typów](../../cpp/user-defined-type-conversions-cpp.md).  
  
3.  Ten problem może wystąpić, gdy podejmowana jest próba można skopiować do wystąpienia klasy zadeklarowany `const` przy użyciu konstruktora kopiującego, który nie przyjmuje `const` odwołać się do parametru. Deklarowanie użytkownika Konstruktor kopiujący z `const` odniesienie zamiast odwołania typu z systemem innym niż stała typu.