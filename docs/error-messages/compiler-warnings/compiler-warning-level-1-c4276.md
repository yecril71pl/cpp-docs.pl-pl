---
title: Kompilator ostrzeżenie (poziom 1) C4276 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4276
dev_langs:
- C++
helpviewer_keywords:
- C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 40a6c85b460e9718a8816598afb016e9c7a493b9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116025"
---
# <a name="compiler-warning-level-1-c4276"></a>Kompilator ostrzeżenie (poziom 1) C4276

'Funkcja': bez prototypu podane; Założono Brak parametrów

Po wykonaniu adresu funkcji z atrybutem [__stdcall](../../cpp/stdcall.md) konwencji wywoływania, musisz udzielić prototyp dzięki czemu kompilator może tworzyć dekorowane nazwy funkcji. Ponieważ *funkcja* ma bez prototypu kompilatora, tworząc nazwę z atrybutami, zakłada się, funkcja nie ma parametrów.