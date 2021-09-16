# Da Vinci File Formats

## GRP - tar-ish type archive

### Header

| Name  | Type  | Description                    |
| ----- | :---: | ------------------------------ |
| nNum  | DWORD | Ammount of entities            |
| dSeek | DWORD | Bytes to Seek untill the start |

### Data

| Name    |      Type      | Description         |
| ------- | :------------: | ------------------- |
| nNameSz |     DWORD      | Size of a NT-String |
| szName  | char\[nNameSz] | File name           |
| iSeek   |     DWORD      | How much to seek    |
| nSize   |     DWORD      | Size of a while     |

---

## CLD - Level bullshit

### Main structure

| Name              |                   Type                   | Description                                                                |
| ----------------- | :--------------------------------------: | -------------------------------------------------------------------------- |
| nHintLen          |                  DWORD                   | Length of hint string                                                      |
| sHint             |             char\[nHintLen]              | Hint string (texture name)                                                 |
| nMetallicLen      |                  DWORD                   | Ammount of balls to describe metallic features                             |
| iSpawnBalls       |                  DWORD                   | Ammount of balls to spawn                                                  |
| _                 |                char\[4*3]                | Padding                                                                    |
| aMetallicFeatures |           DWORD\[nMetallicLen]           | Makes balls half-metallic if 1                                             |
| _                 |             char\[10\*4\*2]              | Padding                                                                    |
| nEntClusters      |                  DWORD                   | Ammount of item clusters                                                   |
| aEntClusters      |        EntCluster\[nEntClusters]         | Entity clusters themselves                                                 |
| aDimensions       |                DWORD\[2]                 | X and Y Dimensions (always 20,20 in real world, but engine allows dynamic) |
| aLevel            | Cell\[aDimensions\[0]]\[aDimensions\[0]] | Level data itself                                                          |

### EntCluster

| Name  |    Type     | Description                        |
| ----- | :---------: | ---------------------------------- |
| _     | char\[4*2]  | Padding                            |
| nEnts |    DWORD    | Ammount of entities in the cluster |
| aEnts | Ent\[nEnts] | Actual entities                    |

### Ent

| Name     |    Type     | Description                                         |
| -------- | :---------: | --------------------------------------------------- |
| bMovable |    DWORD    | Can this entity be moved?                           |
| iPos     |  DWORD\[2]  | (X,Y) positions                                     |
| iEntID   |    DWORD    | Actual entity ID                                    |
| iData4   |    DWORD    | Doesn't do shit                                     |
| iLockNum |    DWORD    | IDK, but appears to be number of the lock           |
| bFadeout |    DWORD    | If not 0, disable fadeout on goal                   |
| nLen     |    DWORD    | Length of the texture name                          |
| sTexture | char\[nLen] | Texture name, GAME DOESN\`T RENDER ALL OF THEM HERE |

### Cell

| Name      | Type  | Description                                      |
| --------- | :---: | ------------------------------------------------ |
| iCellType | DWORD | Cell type                                        |
| bHidden   | DWORD | Is this cell a non playable space?               |
| bChains   | DWORD | Is this ball chained?                            |
| iColour   | DWORD | Colour of this prize                             |
| iPad      | DWORD | Isn't referenced in the game even? (aka padding) |
| bMetal    | DWORD | Is this ball full metall?                        |

> **!!! P.S. THIS GAME APPEARS TO BE ABLE TO SPAWN BALLS/PRIZES EVEN IF ENTITY TYPE IS NOT 0 OR 1, SO BE CAREFUL !!!**
