---
title: Local (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.local
helpviewer_keywords:
- local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
ms.openlocfilehash: d3710eee748a43a1daa5c07d8b3feb6beb8f64fa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214750"
---
# <a name="local-c"></a>local (C++)

W przypadku użycia w nagłówku interfejsu, umożliwia użycie kompilatora MIDL jako generatora nagłówka. W przypadku użycia w pojedynczej funkcji określa procedurę lokalną, dla której nie są generowane żadne wycinki.

## <a name="syntax"></a>Składnia

```cpp
[local]
```

## <a name="remarks"></a>Uwagi

Atrybut **lokalny** C++ ma takie same funkcje jak [lokalny](/windows/win32/Midl/local) atrybut MIDL.

## <a name="example"></a>Przykład

Zobacz [call_as](call-as.md) , aby zapoznać się z przykładem użycia **lokalnego**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**interfejs**, metoda interfejsu|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|None|
|**Nieprawidłowe atrybuty**|`dispinterface`|

Aby uzyskać więcej informacji, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)<br/>
[Atrybuty metody](method-attributes.md)<br/>
[call_as](call-as.md)
