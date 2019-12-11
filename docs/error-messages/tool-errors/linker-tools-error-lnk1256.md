---
title: Błąd narzędzi konsolidatora LNK1256
ms.date: 11/04/2016
f1_keywords:
- LNK1256
helpviewer_keywords:
- LNK1256
ms.assetid: 55b64b2b-a56b-436c-a55e-ec9c6dcb050e
ms.openlocfilehash: bedf96262944d59737a39a942021cdec9445f3b8
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990947"
---
# <a name="linker-tools-error-lnk1256"></a>Błąd narzędzi konsolidatora LNK1256

Operacja ALINK nie powiodła się: Przyczyna

Typowy powód LNK1256 jest nieprawidłowym numerem wersji dla zestawu. Wartość 65535 nie jest dozwolona dla żadnej części numeru wersji zestawu. Prawidłowy zakres wersji zestawu to 0-65534.

LNK1256 może również być przyczyną, jeśli ALINK nie mógł znaleźć nazwanego kontenera kluczy. Usuń kontener kluczy i dodaj go ponownie do dostawcy usług kryptograficznych silnej nazwy przy użyciu [SN. exe (Narzędzie silnej nazwy)](/dotnet/framework/tools/sn-exe-strong-name-tool).

Kolejną przyczyną LNK1256 jest niezgodność wersji między konsolidatorem a Alink. dll. Może to być spowodowane uszkodzeniem instalacji programu Visual Studio. Napraw lub ponownie zainstaluj program Visual Studio za pomocą **apletu programy i funkcje** w panelu sterowania systemu Windows.

Poniższy przykład generuje LNK1256:

```cpp
// LNK1256.cpp
// compile with: /clr /LD
// LNK1256 expected
[assembly:System::Reflection::AssemblyVersionAttribute("1.0.65535")];
public class CMyClass {
public:
   int value;
};
```
