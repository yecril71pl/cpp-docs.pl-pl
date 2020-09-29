---
title: Błąd kompilatora C2026
description: Opisuje C2026 błędów kompilatora Microsoft C/C++, jej przyczyny i sposoby ich rozwiązywania.
ms.date: 09/25/2020
f1_keywords:
- C2026
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
ms.openlocfilehash: 39195568f964f07c6131fa43ef4a0f06121795da
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414051"
---
# <a name="compiler-error-c2026"></a>Błąd kompilatora C2026

> ciąg zbyt długi, obcięto końcowe znaki

Ciąg jest dłuższy niż limit 16380 znaków jednobajtowych.

## <a name="remarks"></a>Uwagi

Przed przekazaniem sąsiednich ciągów ciąg nie może być dłuższy niż 16380 znaków jednobajtowych.

Ciąg Unicode o około jednej połowie tej długości również generuje ten błąd.

## <a name="example"></a>Przykład

Jeśli masz zdefiniowany ciąg w następujący sposób, generuje on C2026:

```C
char sz[] =
"\
imagine a really, really \
long string here\
";
```

Można to zrobić w następujący sposób:

```C
char sz[] =
"\
imagine a really, really "
"long string here\
";
```

Warto przechowywać wyjątkowo duże literały ciągu (32 KB lub więcej) w niestandardowym lub zewnętrznym pliku. Aby uzyskać więcej informacji, zobacz [Tworzenie nowego zasobu niestandardowego lub danych](../../windows/binary-editor.md#to-create-a-new-custom-or-data-resource).
