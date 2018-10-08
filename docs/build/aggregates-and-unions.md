---
title: Agregacje i unie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- aggregates [C++], and unions
ms.assetid: 859fc211-b111-4f12-af98-de78e48f9b92
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aac6da94a0786e5cdc2eee4d16f5927f66e0a8d5
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861190"
---
# <a name="aggregates-and-unions"></a>Agregacje i unie

Inne typy, takie jak tablice, struktur i Unii, ma bardziej rygorystyczne wymagania wyrównania, zapewniający spójny Unii i agregacji magazynem i danymi pobierania. Definicje dla tablic, struktury i Unii są następujące:

- Tablica

   Zawiera grupę uporządkowane obiekty sąsiadujące danych. Każdy obiekt jest nazywany elementu. Wszystkie elementy w tablicy mają ten sam rozmiar i typ danych.

- Struktura

   Zawiera grupę uporządkowane obiektów danych. W odróżnieniu od elementów tablicy obiektów danych w ramach struktury może mieć różne typy danych i rozmiary. Każdy obiekt danych w strukturze nosi nazwę członka.

- Union

   Obiekt, który zawiera jeden zestaw nazwanych elementów członkowskich. Nazwany zestaw elementów członkowskich mogą być dowolnego typu. Magazyn przydzielony dla Unii jest równy magazynu wymaganego dla największego elementu członkowskiego tej Unii, a także wszelkie dopełnienie wymaganych do wyrównania.

W poniższej tabeli przedstawiono silnie sugerowane wyrównanie skalarne elementów członkowskich Unii i struktur.

||||
|-|-|-|
|Typ skalarny|Typ danych C|Wymagane wyrównania|
|**INT8**|**char**|Byte|
|**UINT8**|**unsigned char**|Byte|
|**INT16**|**short**|Word|
|**UINT16**|**short bez znaku**|Word|
|**INT32**|**int**, **długi**|Bitowego|
|**UINT32**|**unsigned int, niepodpisane długa**|Bitowego|
|**INT64**|**__int64**|Quadword|
|**UINT64 —**|**__int64 bez znaku**|Quadword|
|**FP32 (Pojedyncza precyzja)**|**float**|Bitowego|
|**FP64 (Podwójna precyzja)**|**double**|Quadword|
|**WSKAŹNIK**|<strong>\*</strong>|Quadword|
|**__m64**|**__m64 — struktura**|Quadword|
|**__m128**|**__m128 — struktura**|Octaword|

Obowiązują następujące reguły wyrównanie agregacji:

- Wyrównanie w tablicy jest taka sama jak wyrównanie elementów tablicy.

- Wyrównanie początku struktury lub Unii jest maksymalna wyrównanie dowolnego członka. Każdy element członkowski w obrębie struktury lub Unii muszą być umieszczone na jego odpowiednie wyrównanie, zgodnie z definicją w poprzedniej tabeli, które mogą wymagać niejawne dopełnienie wewnętrzne, w zależności od poprzedniego elemenut Członkowskiego.

- Rozmiar struktury musi być wielokrotnością jego wyrównania, która może wymagać dopełnienie po ostatni element członkowski. Ponieważ struktur i Unii mogą być grupowane w tablicach, każdego elementu tablicy, struktury lub Unii należy rozpocząć i końcu prawidłowego wyrównania wcześniej określona.

- Istnieje możliwość wyrównanie danych w taki sposób, aby być większa niż wymagania wyrównania, tak długo, jak poprzednich zasad są obsługiwane.

- Poszczególne kompilator może dostosować pakowanie struktury powodów rozmiar. Na przykład [/ZP (wyrównanie członka struktury)](../build/reference/zp-struct-member-alignment.md) umożliwia dostosowanie pakowanie struktur.

## <a name="see-also"></a>Zobacz też

[Typy i magazyn](../build/types-and-storage.md)
