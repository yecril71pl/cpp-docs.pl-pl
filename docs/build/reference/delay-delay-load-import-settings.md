---
title: /DELAY (Ustawienia opóźnienia importowania ładowania)
ms.date: 11/04/2016
f1_keywords:
- /delay
- VC.Project.VCLinkerTool.DelayNoBind
- VC.Project.VCLinkerTool.SupportUnloadOfDelayLoadedDLL
- VC.Project.VCLinkerTool.DelayUnload
helpviewer_keywords:
- delayed loading of DLLs, /DELAY option
- DELAY linker option
- /DELAY linker option
- -DELAY linker option
ms.assetid: 9334b332-cc58-4dae-b10f-a4c75972d50c
ms.openlocfilehash: edf15d17f0ae6f3bd04b6ed97095594eaebbf675
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565987"
---
# <a name="delay-delay-load-import-settings"></a>/DELAY (Ustawienia opóźnienia importowania ładowania)

```
/DELAY:UNLOAD
/DELAY:NOBIND
```

## <a name="remarks"></a>Uwagi

Przełącznik/DELAY — opcja formanty [opóźnione ładowanie](../../build/reference/linker-support-for-delay-loaded-dlls.md) bibliotek DLL:

- Kwalifikator UNLOAD informuje funkcję pomocnika obciążenia opóźnienia, aby wspierała jawne zwalnianie biblioteki DLL. Tabeli adresów importowania (IAT) jest resetowany do ich oryginalnej formie, co unieważniło IAT wskaźników i powoduje zastąpienie.

   W przypadku niewybrania zwolnienie żadnym wywołaniu, aby [FUnloadDelayLoadedDLL](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md) zakończy się niepowodzeniem.

- Kwalifikator NOBIND informuje konsolidator, nie można dołączyć powiązania IAT do obrazu końcowego. Wartość domyślna to można utworzyć powiązania IAT dla bibliotek DLL załadowanych z opóźnieniem. Obraz wynikowy nie można powiązać statycznie. (Obrazy o możliwej do wiązania IATs może zostać statycznie powiązane przed wykonaniem.) Zobacz [/BIND](../../build/reference/bind.md).

   Jeśli biblioteka DLL jest związany, funkcji pomocnika zostanie podjęta próba wykorzystania powiązane informacje, zamiast wywoływać metodę [GetProcAddress](/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress) na wszystkich importów odwołania. Jeśli sygnaturę czasową lub preferowany adres nie odpowiadają załadowanej biblioteki dll, funkcja pomocnika przyjmie IAT powiązanej jest nieaktualna i będzie kontynuowane tak, jakby powiązanej IAT nie istnieje.

   NOBIND powoduje, że program obrazu będzie większy, ale można przyspieszyć ładowanie czasu biblioteki dll. Jeśli nigdy nie zamierzasz powiązać biblioteki DLL, NOBIND uniemożliwi powiązanej IAT generowany.

Aby określić bibliotek DLL w celu opóźnienia ładowania, należy użyć [/delayload](../../build/reference/delayload-delay-load-import.md) opcji.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać informacje, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji**, **konsolidatora**, a następnie wybierz pozycję **zaawansowane**.

1. Modyfikowanie **bibliotek DLL załadowanych opóźnienie** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)