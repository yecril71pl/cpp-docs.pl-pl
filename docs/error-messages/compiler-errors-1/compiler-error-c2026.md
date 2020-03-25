---
title: Błąd kompilatora C2026
ms.date: 11/04/2016
f1_keywords:
- C2026
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
ms.openlocfilehash: 9747b1edadc76ceeb502b2c6fd03496b91769f5a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208068"
---
# <a name="compiler-error-c2026"></a>Błąd kompilatora C2026

ciąg zbyt długi, obcięto końcowe znaki

Ciąg jest dłuższy niż limit 16380 znaków jednobajtowych.

Przed połączeniem sąsiednich ciągów ciąg nie może zawierać więcej niż 16380 znaków jednobajtowych.

Ciąg Unicode o około jednej połowie tej długości również generuje ten błąd.

Jeśli masz zdefiniowany ciąg w następujący sposób, generuje on C2026:

```
char sz[] =
"\
imagine a really, really \
long string here\
";
```

Można to zrobić w następujący sposób:

```
char sz[] =
"\
imagine a really, really "
"long string here\
";
```

Warto przechowywać wyjątkowo duże literały ciągu (32 KB lub więcej) w niestandardowym lub zewnętrznym pliku. Aby uzyskać więcej informacji [, zobacz Tworzenie nowego niestandardowego lub zasobu danych](../../windows/creating-a-new-custom-or-data-resource.md) .
