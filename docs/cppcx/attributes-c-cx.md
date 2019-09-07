---
title: Atrybuty (C++/CX)
ms.date: 12/30/2016
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
ms.openlocfilehash: 77962dc2d4b7f6bda90a5376e5154782365a4106
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740382"
---
# <a name="attributes-ccx"></a>Atrybuty (C++/CX)

Atrybut jest specjalnym rodzajem klasy referencyjnej, które można dołączać w nawiasach kwadratowych do środowisko wykonawcze systemu Windows typów i metod w celu określenia niektórych zachowań w tworzeniu metadanych. Kilka wstępnie zdefiniowanych atrybutów — na przykład [Windows:: Foundation:: Metadata:: WebHostHidden](/uwp/api/Windows.Foundation.Metadata.WebHostHiddenAttribute)— są często używane w C++kodzie/CX. Ten przykład pokazuje, jak atrybut jest stosowany do klasy:

[!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]

## <a name="custom-attributes"></a>Atrybuty niestandardowe

Można również zdefiniować atrybuty niestandardowe. Atrybuty niestandardowe muszą być zgodne z tymi środowisko wykonawcze systemu Windows regułami:

- Atrybuty niestandardowe mogą zawierać tylko pola publiczne.

- Pola atrybutów niestandardowych mogą być inicjowane, gdy atrybut jest stosowany do klasy.

- Pole może być jednym z następujących typów:

   - Int32 (int)

   - UInt32 (bez znaku int)

   - bool

   - Platform:: String ^

   - Windows::Foundation::HResult

   - Platforma:: wpisz ^

   - publiczna Klasa enum (zawiera wyliczenia zdefiniowane przez użytkownika)

W następnym przykładzie pokazano, jak zdefiniować atrybut niestandardowy, a następnie zainicjować go podczas korzystania z niego.

[!code-cpp[cx_attributes#02](../cppcx/codesnippet/CPP/cx_attributes/class1.h#02)]

## <a name="see-also"></a>Zobacz także

[System typów (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
