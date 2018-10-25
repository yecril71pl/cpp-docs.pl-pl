---
title: Identyfikator UUID (atrybuty C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.uuid
dev_langs:
- C++
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3eddf1981aba8babcb87562ed546ce4086499fd7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071342"
---
# <a name="uuid-c-attributes"></a>uuid (Atrybuty C++)

Określa unikatowy identyfikator dla klasy lub interfejsu.

## <a name="syntax"></a>Składnia

```cpp
[ uuid(
   "uuid"
) ]
```

### <a name="parameters"></a>Parametry

*uuid*<br/>
128-bitowego, unikatowy identyfikator.

## <a name="remarks"></a>Uwagi

Jeśli nie określono definicji klasy lub interfejsu **uuid** atrybutów języka C++, a następnie kompilator języka Visual C++ zapewni jeden. Po określeniu **uuid**, musi zawierać cudzysłowów.

Jeśli nie określisz **uuid**, a następnie kompilator wygeneruje tego samego identyfikatora GUID dla interfejsów lub klas o takiej samej nazwie w projektach innego atrybutu na maszynie.

Uuidgen.exe lub Guidgen.exe służy do generowania własnych unikatowych identyfikatorów. (Aby Uruchom dowolne z tych narzędzi, kliknij przycisk **Start** i kliknij przycisk **Uruchom** w menu. Następnie wprowadź nazwę wymagane narzędzia.)

W przypadku użycia w projekcie, który nie używa również biblioteki ATL, określając **uuid** atrybutu jest taki sam jak określanie [uuid](../../cpp/uuid-cpp.md) **__declspec** modyfikator. Aby pobrać **uuid** klasy, można użyć [__uuidof](../../cpp/uuidof-operator.md)

## <a name="example"></a>Przykład

Zobacz [możliwej do wiązania](bindable.md) przykład użycie próbki **uuid**.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa**, **struktury**, **interfejsu**, **Unii**, **wyliczenia**|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty IDL](idl-attributes.md)<br/>
[Atrybuty interfejsu](interface-attributes.md)<br/>
[Atrybuty klasy](class-attributes.md)<br/>
[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[uuid](/windows/desktop/Midl/uuid)