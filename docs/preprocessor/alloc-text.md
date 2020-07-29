---
title: alloc_text pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.alloc_text
- alloc_text_CPP
helpviewer_keywords:
- alloc_text pragma
- pragmas, alloc_text
ms.assetid: 1fd7be18-e4f7-4f70-b079-6326f72b871a
ms.openlocfilehash: c638c2026a493453aeb5aff00ba6273efb5f184e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219446"
---
# <a name="alloc_text-pragma"></a>alloc_text pragma

Nazwa sekcji kodu, w której znajdują się określone definicje funkcji. Dyrektywa pragma musi występować między funkcją deklarator i definicją funkcji dla nazwanych funkcji.

## <a name="syntax"></a>Składnia

> **#pragma alloc_text (** "*textsection*" **,** *function1* [**,** *function2* ...] **)**

## <a name="remarks"></a>Uwagi

Dyrektywa pragma **alloc_text** nie obsługuje funkcji składowych języka C++ ani przeciążonych funkcji. Ma zastosowanie tylko do funkcji zadeklarowanych za pomocą powiązania C — to znaczy, że funkcje zadeklarowane ze specyfikacją powiązania **extern "C"** . Jeśli spróbujesz użyć tej dyrektywy pragma w funkcji z powiązaniem języka C++, zostanie wygenerowany błąd kompilatora.

Ponieważ adresowanie funkcji przy użyciu **`__based`** nie jest obsługiwane, określenie lokalizacji sekcji wymaga zastosowania dyrektywy pragma **alloc_text** . Nazwa określona przez *textsection* powinna być ujęta w znaki podwójnego cudzysłowu.

Dyrektywa pragma **alloc_text** musi występować po deklaracjach którejkolwiek z określonych funkcji i przed definicjami tych funkcji.

Funkcje, do których odwołuje się **alloc_text** pragma, powinny być zdefiniowane w tym samym module co pragma. W przeciwnym razie, jeśli Niezdefiniowana funkcja zostanie później skompilowana do innej sekcji tekstu, błąd może lub nie zostać przechwycony. Mimo że program jest zwykle uruchamiany poprawnie, funkcja nie zostanie przypisana w zamierzonych sekcjach.

Inne ograniczenia dotyczące **alloc_text** są następujące:

- Nie można jej użyć wewnątrz funkcji.

- Musi być używany po zadeklarowaniu funkcji, ale przed zdefiniowaniem funkcji.

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
