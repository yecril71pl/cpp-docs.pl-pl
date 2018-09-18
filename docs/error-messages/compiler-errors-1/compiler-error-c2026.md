---
title: Błąd kompilatora C2026 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2026
dev_langs:
- C++
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 055ac47d036a1027817aa6b3433bfe0e2e88570e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019552"
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