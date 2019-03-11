---
title: Flagi kontrolne
ms.date: 11/04/2016
f1_keywords:
- c.flags
helpviewer_keywords:
- flags, control
- heap allocation, control flags
- debug heap, control flags
ms.assetid: 8dbd24a5-0633-42d1-9771-776db338465f
ms.openlocfilehash: 7ac5f239ea4d242618fb23ba617a3a6539492053
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750117"
---
# <a name="control-flags"></a>Flagi kontrolne

Wersja do debugowania biblioteki wykonawczej C firmy Microsoft korzysta z następujących flag do kontroli Alokacja sterty i proces raportowania. Aby uzyskać więcej informacji, zobacz [techniki testowania CRT](/visualstudio/debugger/crt-debugging-techniques).

|Flaga|Opis|
|----------|-----------------|
|[_CRTDBG_MAP_ALLOC](../c-runtime-library/crtdbg-map-alloc.md)|Mapuje ich odpowiedniki wersji debugowania funkcji stosu podstawowego|
|[_DEBUG](../c-runtime-library/debug.md)|Umożliwia korzystanie z wersji debugowania funkcji wykonawczej|
|[_crtDbgFlag](../c-runtime-library/crtdbgflag.md)|Określa, jak Menedżer stosu debugowania śledzi alokacje|

Te flagi mogą być definiowane za pomocą opcji wiersza polecenia/d. lub za pomocą `#define` dyrektywy. Jeśli flaga jest zdefiniowana za pomocą `#define`, dyrektywa musi znajdować się przed plik nagłówkowy obejmują instrukcji dla procedury deklaracji.

## <a name="see-also"></a>Zobacz także

[Zmienne globalne i typy standardowe](../c-runtime-library/global-variables-and-standard-types.md)
