---
title: Błąd kompilatora C2026
ms.date: 11/04/2016
f1_keywords:
- C2026
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
ms.openlocfilehash: da4c03c681f95efaa5edb159869315b41d027e99
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303531"
---
# <a name="compiler-error-c2026"></a>Błąd kompilatora C2026

ciąg zbyt długi, obcięto końcowe znaki

Ciąg znaków był dłuższy niż limit 16380 znaków jednobajtowych.

Przed ciągów sąsiadujących są łączone ciąg nie może być dłuższa niż 16380 znaków jednobajtowych.

Ciąg Unicode długości połowy ten będzie również wygenerować ten błąd.

Jeśli masz ciąg, który został zdefiniowany w następujący sposób, generuje C2026:

```
char sz[] =
"\
imagine a really, really \
long string here\
";
```

Użytkownik może Podziel je w następujący sposób:

```
char sz[] =
"\
imagine a really, really "
"long string here\
";
```

Warto przechowywać literałów ciągów wyjątkowo dużą (32 KB lub więcej) zasobów niestandardowych lub zewnętrznego pliku. Zobacz [Tworzenie nowej niestandardowej lub zasobów danych](../../windows/creating-a-new-custom-or-data-resource.md) Aby uzyskać więcej informacji.