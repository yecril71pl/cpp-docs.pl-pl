---
title: Ostrzeżenie RC4005 kompilatora zasobów
ms.date: 11/04/2016
f1_keywords:
- RC4005
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
ms.openlocfilehash: c428fefa90cceed6a8bc9b7f6e4b95ec2db5e039
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182412"
---
# <a name="resource-compiler-warning-rc4005"></a>Ostrzeżenie RC4005 kompilatora zasobów

"Identyfikator": Ponowna definicja makra

Identyfikator jest definiowany dwa razy. Kompilator użył drugiej definicji makra.

To ostrzeżenie może być spowodowane przez zdefiniowanie makra w wierszu polecenia i w kodzie z dyrektywą `#define`. Przyczyną może być również makra importowane z plików dołączanych.

Aby wyeliminować ostrzeżenie, Usuń jedną z definicji lub użyj dyrektywy `#undef`ej przed drugą definicją.
