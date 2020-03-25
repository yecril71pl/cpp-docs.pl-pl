---
title: Błąd krytyczny CVTRES CVT1100
ms.date: 11/04/2016
f1_keywords:
- CVT1100
helpviewer_keywords:
- CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
ms.openlocfilehash: b7e67df24d41b1e8826673146fcc27fd93d143fd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196550"
---
# <a name="cvtres-fatal-error-cvt1100"></a>Błąd krytyczny CVTRES CVT1100

zduplikowany zasób — typ: wpisz, Name: Name, language: language, flags: flags, size: size

Podany zasób został określony więcej niż raz.

Ten błąd może wystąpić, jeśli konsolidator tworzy bibliotekę typów i nie określono [/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md) , a zasób w projekcie używa już 1. W takim przypadku należy określić/TLBID i określić inną liczbę do 65535.
