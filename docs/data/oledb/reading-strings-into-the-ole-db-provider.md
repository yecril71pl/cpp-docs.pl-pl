---
title: Wczytywanie ciągów do dostawcy OLE DB
ms.date: 10/13/2018
helpviewer_keywords:
- OLE DB providers, reading strings into
ms.assetid: 517f322c-f37e-4eed-bf5e-dd9a412c2f98
ms.openlocfilehash: 50df9f13b814eb00b309460894d704238bc3e7dc
ms.sourcegitcommit: 943c792fdabf01c98c31465f23949a829eab9aad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "51264779"
---
# <a name="reading-strings-into-the-ole-db-provider"></a>Wczytywanie ciągów do dostawcy OLE DB

`CCustomRowset::Execute` Funkcji otwiera plik i odczytuje ciągi. Konsument przekazuje nazwę pliku do dostawcy, wywołując [ICommandText::SetCommandText](/previous-versions/windows/desktop/ms709757). Dostawca otrzymuje nazwę pliku i zapisuje go w zmiennej składowej `m_strCommandText`. `Execute` odczytuje nazwę pliku z `m_strCommandText`. Jeśli nazwa pliku jest nieprawidłowa lub plik jest niedostępny, `Execute` zwraca błąd. W przeciwnym razie zostanie otwarty plik i wywołania `fgets` można pobrać ciągów. Dla każdego zestawu ciągów jej operacje odczytu, `Execute` tworzy wystąpienie rekord użytkownika (zmodyfikowany `CCustomWindowsFile` z [przechowywanie ciągów w dostawcy OLE DB](../../data/oledb/storing-strings-in-the-ole-db-provider.md)) i umieszcza je w tablicy.

Jeśli nie można otworzyć pliku, `Execute` musi zwracać DB_E_NOTABLE. Jeśli zamiast tego zwraca E_FAIL, dostawca nie będzie działać z wielu odbiorców i nie przekaże OLE DB [testów zgodności](../../data/oledb/testing-your-provider.md).

## <a name="example"></a>Przykład

```cpp
/////////////////////////////////////////////////////////////////////////
// CustomRS.h
class CCustomRowset : public CRowsetImpl< CCustomRowset, CCustomWindowsFile, CCustomCommand>
{
public:
    HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)
    {
        enum {
            sizeOfBuffer = 256,
            sizeOfFile = MAX_PATH
        };
        USES_CONVERSION;
        FILE* pFile = NULL;
        TCHAR szString[sizeOfBuffer];
        TCHAR szFile[sizeOfFile];
        size_t nLength;

        ObjectLock lock(this);

        // From a filename, passed in as a command text, scan the file
        // placing data in the data array.
        if (!m_strCommandText)
        {
            ATLTRACE("No filename specified");
            return E_FAIL;
        }

        // Open the file
        _tcscpy_s(szFile, sizeOfFile, m_strCommandText);
        if (szFile[0] == _T('\0') ||
            (fopen_s(&pFile, (char*)&szFile[0], "r") == 0))
        {
            ATLTRACE("Could not open file");
            return DB_E_NOTABLE;
        }

        // Scan and parse the file.
        // The file should contain two strings per record
        LONG cFiles = 0;
        while (fgets((char*)szString, sizeOfBuffer, pFile) != NULL)
        {
            nLength = strnlen((char*)szString, sizeOfBuffer);
            szString[nLength-1] = '\0';   // Strip off trailing CR/LF
            CCustomWindowsFile am;
            _tcscpy_s(am.szCommand, am.iSize, szString);
            _tcscpy_s(am.szCommand2, am.iSize, szString);

            if (fgets((char*)szString, sizeOfBuffer, pFile) != NULL)
            {
                nLength = strnlen((char*)szString, sizeOfBuffer);
                szString[nLength-1] = '\0'; // Strip off trailing CR/LF
                _tcscpy_s(am.szText, am.iSize, szString);
                _tcscpy_s(am.szText2, am.iSize, szString);
            }

            am.dwBookmark = ++cFiles;
            if (!m_rgRowData.Add(am))
            {
                ATLTRACE("Couldn't add data to array");
                fclose(pFile);
                return E_FAIL;
            }
        }

        if (pcRowsAffected != NULL)
            *pcRowsAffected = cFiles;
        return S_OK;
    }
};
```

Gdy jest to wykonywane, dostawca powinien być gotowe do kompilowania i uruchamiania. Aby przetestować dostawcę, należy odbiorców za pomocą funkcji dopasowywania. [Implementowanie prostego konsumenta](../../data/oledb/implementing-a-simple-consumer.md) pokazuje, jak utworzyć odbiorcę testu. Uruchom klienta testowego z dostawcą i sprawdź, czy konsumenta test pobiera odpowiednie ciągi od dostawcy.

Twój dostawca zostały pomyślnie przetestowane, można zwiększyć jego działanie, implementując dodatkowe interfejsy. Przykład został przedstawiony na [udoskonalanie prostego dostawcy tylko do odczytu](../../data/oledb/enhancing-the-simple-read-only-provider.md).

## <a name="see-also"></a>Zobacz też

[Implementowanie prostego dostawcy tylko do odczytu](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
