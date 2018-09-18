---
title: Błąd krytyczny C1853 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: error-reference
f1_keywords:
- C1853
dev_langs:
- C++
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 016e5bbf064643ddff0f63c5e16a967ed914f3e2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044954"
---
# <a name="fatal-error-c1853"></a>Błąd krytyczny C1853

> "*filename*" prekompilowanego pliku nagłówkowego pochodzi z poprzedniej wersji kompilatora lub prekompilowany plik nagłówkowy jest w języku C++ i używania go z C (lub odwrotnie)

Możliwe przyczyny:

- Prekompilowany plik nagłówkowy został skompilowany przy użyciu poprzedniej wersji kompilatora. Spróbuj ponownej kompilacji nagłówka z bieżącym kompilatora.

- Prekompilowany plik nagłówkowy jest w języku C++ i korzystają z C. Spróbuj ponownej kompilacji nagłówka do użycia przy użyciu języka C, określając jedną z [TP](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) opcje kompilatora lub zmiana sufiksu pliku źródłowego "c". Aby uzyskać więcej informacji, zobacz [dwa wybory dla wstępnej kompilacji kodu](../../build/reference/creating-precompiled-header-files.md#two-choices-for-precompiling-code).