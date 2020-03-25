---
title: Ostrzeżenie kompilatora (poziom 1) C4651
ms.date: 11/04/2016
f1_keywords:
- C4651
helpviewer_keywords:
- C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
ms.openlocfilehash: bc8131665c970c3b86bb1e84e39636ae8f93897b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199545"
---
# <a name="compiler-warning-level-1-c4651"></a>Ostrzeżenie kompilatora (poziom 1) C4651

określono element "Definition" dla prekompilowanego nagłówka, ale nie dla bieżącego kompilowania

Definicja została określona podczas generowania prekompilowanego nagłówka, ale nie w tej kompilacji.

Definicja będzie obowiązywać w prekompilowanym nagłówku, ale nie w pozostałej części kodu.

W przypadku skompilowania prekompilowanego nagłówka z/DSYMBOL, kompilator generuje to ostrzeżenie, jeśli kompilacja/Yu nie ma/DSYMBOL.  Dodanie/DSYMBOL do wiersza polecenia/Yu rozwiązuje to ostrzeżenie.
