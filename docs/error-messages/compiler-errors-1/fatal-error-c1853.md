---
title: Błąd krytyczny C1853
ms.date: 11/04/2016
f1_keywords:
- C1853
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
ms.openlocfilehash: ec2d6bf6bac46cca8bdc2e3b8fe7cc6b7799d78a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820731"
---
# <a name="fatal-error-c1853"></a>Błąd krytyczny C1853

> "*filename*" prekompilowanego pliku nagłówkowego pochodzi z poprzedniej wersji kompilatora lub prekompilowany plik nagłówkowy jest w języku C++ i używania go z C (lub odwrotnie)

Możliwe przyczyny:

- Prekompilowany plik nagłówkowy został skompilowany przy użyciu poprzedniej wersji kompilatora. Spróbuj ponownej kompilacji nagłówka z bieżącym kompilatora.

- Prekompilowany plik nagłówkowy jest w języku C++ i korzystają z C. Spróbuj ponownej kompilacji nagłówka do użycia przy użyciu języka C, określając jedną z [TP](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) opcje kompilatora lub zmiana sufiksu pliku źródłowego "c". Aby uzyskać więcej informacji, zobacz [dwa wybory dla wstępnej kompilacji kodu](../../build/creating-precompiled-header-files.md#two-choices-for-precompiling-code).