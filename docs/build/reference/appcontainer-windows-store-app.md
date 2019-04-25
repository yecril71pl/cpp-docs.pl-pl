---
title: / APPCONTAINER (aplikacja platformy uniwersalnej systemu Windows/Microsoft Store)
ms.date: 11/04/2016
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
ms.openlocfilehash: f7ab8cf1ce034580953fdf1403264e8ef3d3ff09
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295123"
---
# <a name="appcontainer-microsoft-store-app"></a>/ APPCONTAINER (aplikacja Microsoft Store)

Określa, czy program łączący tworzy obraz wykonywalny, który musi być uruchamiany w kontenerze aplikacji.

## <a name="syntax"></a>Składnia

```
/APPCONTAINER[:NO]
```

## <a name="remarks"></a>Uwagi

Domyślnie/appcontainer jest wyłączona.

Opcja ta modyfikuje plik wykonywalny, wskazując, czy aplikacja musi zostać uruchomiony w środowisku izolacji procesu kontenera aplikacji. Określa przełącznik/appcontainer dla aplikacji, które należy uruchomić w środowisku kontenera aplikacji — na przykład, Universal Windows Uniwersalnej systemu Windows Phone 8.x aplikacją lub. (Opcja jest ustawiana automatycznie w programie Visual Studio podczas tworzenia aplikacji Windows Universal z szablonu.) Aplikacji klasycznej należy określić/appcontainer: no lub po prostu pominąć opcję.

Opcja/appcontainer została wprowadzona w systemie Windows 8.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji** węzła.

1. Rozwiń **konsolidatora** węzła.

1. Wybierz **wiersza polecenia** stronę właściwości.

1. W **dodatkowe opcje**, wprowadź `/APPCONTAINER` lub `/APPCONTAINER:NO`.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
