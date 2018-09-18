---
title: Flagi kontrolne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.flags
dev_langs:
- C++
helpviewer_keywords:
- flags, control
- heap allocation, control flags
- debug heap, control flags
ms.assetid: 8dbd24a5-0633-42d1-9771-776db338465f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 716e597be5d337d11d58df944bbba468e496f078
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078065"
---
# <a name="control-flags"></a>Flagi kontrolne

Wersja do debugowania biblioteki wykonawczej C firmy Microsoft korzysta z następujących flag do kontroli Alokacja sterty i proces raportowania. Aby uzyskać więcej informacji, zobacz [techniki testowania CRT](/visualstudio/debugger/crt-debugging-techniques).

|Flaga|Opis|
|----------|-----------------|
|[_CRTDBG_MAP_ALLOC](../c-runtime-library/crtdbg-map-alloc.md)|Mapuje ich odpowiedniki wersji debugowania funkcji stosu podstawowego|
|[_DEBUG](../c-runtime-library/debug.md)|Umożliwia korzystanie z wersji debugowania funkcji wykonawczej|
|[_crtDbgFlag](../c-runtime-library/crtdbgflag.md)|Określa, jak Menedżer stosu debugowania śledzi alokacje|

Te flagi mogą być definiowane za pomocą opcji wiersza polecenia/d. lub za pomocą `#define` dyrektywy. Jeśli flaga jest zdefiniowana za pomocą `#define`, dyrektywa musi znajdować się przed plik nagłówkowy obejmują instrukcji dla procedury deklaracji.

## <a name="see-also"></a>Zobacz też

[Zmienne globalne i typy standardowe](../c-runtime-library/global-variables-and-standard-types.md)