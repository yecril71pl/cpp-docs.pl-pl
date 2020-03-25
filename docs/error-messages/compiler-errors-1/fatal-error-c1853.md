---
title: Błąd krytyczny C1853
ms.date: 11/04/2016
f1_keywords:
- C1853
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
ms.openlocfilehash: 056db975fecef4e101dbbba7e2084236489498c7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202868"
---
# <a name="fatal-error-c1853"></a>Błąd krytyczny C1853

> prekompilowany plik nagłówkowy "*filename*" pochodzi z poprzedniej wersji kompilatora lub prekompilowany nagłówek jest i jest C++ używany w języku C (lub odwrotnie)

Możliwe przyczyny:

- Prekompilowany nagłówek został skompilowany z poprzednią wersją kompilatora. Spróbuj ponownie skompilować nagłówek przy użyciu bieżącego kompilatora.

- Prekompilowany nagłówek jest C++ używany w języku c. Spróbuj ponownie skompilować nagłówek do użycia z c, określając jedną z opcji kompilatora [/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) lub zmieniając sufiks pliku źródłowego na "c". Aby uzyskać więcej informacji, zobacz [dwie opcje wstępnego kompilowania kodu](../../build/creating-precompiled-header-files.md#two-choices-for-precompiling-code).
