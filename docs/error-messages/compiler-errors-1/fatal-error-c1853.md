---
title: Błąd krytyczny C1853
ms.date: 11/04/2016
f1_keywords:
- C1853
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
ms.openlocfilehash: 30cf003cc81cb27f7c68b7f0a38529e2d9c88ef5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677828"
---
# <a name="fatal-error-c1853"></a>Błąd krytyczny C1853

> "*filename*" prekompilowanego pliku nagłówkowego pochodzi z poprzedniej wersji kompilatora lub prekompilowany plik nagłówkowy jest w języku C++ i używania go z C (lub odwrotnie)

Możliwe przyczyny:

- Prekompilowany plik nagłówkowy został skompilowany przy użyciu poprzedniej wersji kompilatora. Spróbuj ponownej kompilacji nagłówka z bieżącym kompilatora.

- Prekompilowany plik nagłówkowy jest w języku C++ i korzystają z C. Spróbuj ponownej kompilacji nagłówka do użycia przy użyciu języka C, określając jedną z [TP](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) opcje kompilatora lub zmiana sufiksu pliku źródłowego "c". Aby uzyskać więcej informacji, zobacz [dwa wybory dla wstępnej kompilacji kodu](../../build/reference/creating-precompiled-header-files.md#two-choices-for-precompiling-code).