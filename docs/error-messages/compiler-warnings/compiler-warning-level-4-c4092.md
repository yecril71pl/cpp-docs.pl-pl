---
title: Kompilatora (poziom 4) ostrzeżenie C4092
ms.date: 11/04/2016
f1_keywords:
- C4092
helpviewer_keywords:
- C4092
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
ms.openlocfilehash: a6949586cf3faa00aafed37a72e58c1b80266cf5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401387"
---
# <a name="compiler-warning-level-4-c4092"></a>Kompilatora (poziom 4) ostrzeżenie C4092

Operator sizeof zwraca "unsigned long"

Argument operacji `sizeof` operator był bardzo duży, dlatego `sizeof` zwracany typ unsigned **długie**. Ostrzeżenie to pojawia się w obszarze rozszerzenia Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)). W obszarze zgodności ANSI (/Za) zamiast tego zostanie obcięta wynik.