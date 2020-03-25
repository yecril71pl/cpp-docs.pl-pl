---
title: Ostrzeżenie kompilatora (poziom 2) C4653
ms.date: 11/04/2016
f1_keywords:
- C4653
helpviewer_keywords:
- C4653
ms.assetid: 90ec3317-3d39-4b4c-bcd1-97e7c799e1b6
ms.openlocfilehash: 994e9a4963e7e10af2313b3dcea5bb8b2b93426e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161740"
---
# <a name="compiler-warning-level-2-c4653"></a>Ostrzeżenie kompilatora (poziom 2) C4653

Opcja kompilatora "Option" jest niespójna z prekompilowanym nagłówkiem; Bieżąca opcja wiersza poleceń została zignorowana

Opcja określona z opcją Użyj prekompilowanych nagłówków ([/Yu](../../build/reference/yu-use-precompiled-header-file.md)) była niespójna z opcjami określonymi podczas tworzenia prekompilowanego nagłówka. Ta kompilacja użyła opcji określonej podczas tworzenia prekompilowanego nagłówka.

To ostrzeżenie może wystąpić, gdy podczas kompilacji prekompilowanego nagłówka określono inną wartość opcji struktury pakietów ([/ZP](../../build/reference/zp-struct-member-alignment.md)).
