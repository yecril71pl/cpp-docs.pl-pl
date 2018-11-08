---
title: Obsługa wolnych wątków w dostawcy
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, multithreaded
- threading [C++], providers
ms.assetid: a91270dc-cdf9-4855-88e7-88a54be7cbe8
ms.openlocfilehash: 14acaa6ad96f74b2a3f88ca366a43caa9199a1d8
ms.sourcegitcommit: 943c792fdabf01c98c31465f23949a829eab9aad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "51265038"
---
# <a name="supporting-free-threading-in-your-provider"></a>Obsługa wolnych wątków w dostawcy

Wszystkie klasy dostawcy OLE DB są odporne na wątki i wpisy rejestru są odpowiednio ustawiane. To dobry pomysł, aby obsługa wolnych wątków w celu zapewnienia wysokiego poziomu wydajności w sytuacjach, w wielu użytkowników. Aby zapewnić dostawcą metodą o bezpiecznych wątkach, należy sprawdzić, czy kod jest zablokowany prawidłowo. Zawsze, gdy zapisu lub przechowywania danych, należy zablokować dostęp za pomocą sekcji krytycznych.

Każdy obiekt szablonu dostawcy OLE DB ma swój własny sekcję krytyczną. Aby łatwiej blokowania, każda nowa klasa tworzenia powinna być klasą szablonu, biorąc klasy nadrzędnej nazwę jako argument.

Poniższy przykład pokazuje, jak zablokować kodu:

```cpp
template <class T>
class CMyObject<T> : public...

HRESULT MyObject::MyMethod(void)
{
   T* pT = (T*)this;      // this gets the parent class

// You don't need to do anything if you are only reading information

// If you want to write information, do the following:
   pT->Lock();         // engages critical section in the object
   ...;                // write whatever information you wish
   pT->Unlock();       // disengages the critical section
}
```

Aby uzyskać więcej informacji o tym, jak chronić krytyczne sekcje z `Lock` i `Unlock`, zobacz [wielowątkowość: jak używać klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

Sprawdź, czy jakiekolwiek metody zastąpisz (takie jak `Execute`) jest metodą o bezpiecznych wątkach.

## <a name="see-also"></a>Zobacz też

[Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)