---
title: Błąd kompilatora C2174 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2174
dev_langs:
- C++
helpviewer_keywords:
- C2174
ms.assetid: 161d563c-76e9-47e9-9142-7812e9ea169e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8a7dc9cee6bf24f4605455818a32bd757bcd60c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052377"
---
# <a name="compiler-error-c2174"></a>Błąd kompilatora C2174

'Funkcja': rzeczywisty parametr jest typu "void": parametr liczba1, liczba2 listy parametrów

Parametr `number1` przekazywane do listy parametrów `number2` jest `void` parametru. Parametry nie może mieć typu `void`. Zamiast nich należy używać słów kluczowych `void*`.