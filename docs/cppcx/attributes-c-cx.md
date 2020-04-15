---
title: Atrybuty (C++/CX)
ms.date: 12/30/2016
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
ms.openlocfilehash: 437432ce32497311a9a91237118d6088881662a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371879"
---
# <a name="attributes-ccx"></a>Atrybuty (C++/CX)

Atrybut jest specjalnym rodzajem ref klasy, które mogą być poprzedzane w nawiasach kwadratowych do typów środowiska wykonawczego systemu Windows i metod, aby określić pewne zachowania w tworzeniu metadanych. Kilka wstępnie zdefiniowanych atrybutów — na przykład [Windows::Foundation::Metadata::WebHostHidden](/uwp/api/Windows.Foundation.Metadata.WebHostHiddenAttribute)— jest często używanych w kodzie C++/CX. W tym przykładzie pokazano, jak atrybut jest stosowany do klasy:

[!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]

## <a name="custom-attributes"></a>Atrybuty niestandardowe

Można również zdefiniować atrybuty niestandardowe. Atrybuty niestandardowe muszą być zgodne z następującymi regułami środowiska wykonawczego systemu Windows:

- Atrybuty niestandardowe mogą zawierać tylko pola publiczne.

- Niestandardowe pola atrybutów można zainicjować, gdy atrybut jest stosowany do klasy.

- Pole może być jednym z następujących typów:

  - int32 (int)

  - uint32 (niepodpisany int)

  - bool

  - Platforma::Ciąg^

  - Windows::Fundacja::HResult

  - Platforma::Typ^

  - klasa wyliczenia publicznego (obejmuje wyliczenia zdefiniowane przez użytkownika)

W następnym przykładzie pokazano, jak zdefiniować atrybut niestandardowy, a następnie zainicjować go, gdy go używasz.

[!code-cpp[cx_attributes#02](../cppcx/codesnippet/CPP/cx_attributes/class1.h#02)]

## <a name="see-also"></a>Zobacz też

[System typów (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Odwołanie do języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
