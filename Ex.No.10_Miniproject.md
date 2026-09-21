# Ex.No: 10  Implementation of 2D/3D game
### DATE:                                                                            
### REGISTER NUMBER : 212224233001
### AIM: 
To develop a 2D game using C# program in Unity. 
### Algorithm:
```
STEP 1:
Create a 2D project in Unity.

STEP 2:
Add player, hurdles, coins, track in the frame and add the valid collider2D component.

STEP 3:
Click Assets -> Create -> # Script.

STEP 4:
Create player.cs and coinmanger.cs script and add C# code.

STEP 5:
Click canvas -> Gamemanager -> add Score and value.

STEP 6:
Drag the script to player and coin.

STEP 7:
Run the scene and display the output.

```  
### Program:
Player.cs
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Player : MonoBehaviour
{
    public float speed, jumpforce;
    private Rigidbody2D rb;
    public Score cc;
    void Start()
    {
        rb = GetComponent<Rigidbody2D>();
    }

    // Update is called once per frame
    void Update()
    {
        float moveinp = Input.GetAxis("Horizontal");
        transform.position += new Vector3(moveinp , 0, 0) * speed * Time.deltaTime;
        if (Input.GetKeyDown(KeyCode.Space) && Mathf.Abs(rb.velocity.y) < 0.001f)
        {
            rb.AddForce(new Vector2(0, jumpforce), ForceMode2D.Impulse);
        }

    }
    
    private void OnTriggerEnter2D(Collider2D other)
    {
        if (other.CompareTag("Destroy"))
        {
            cc.coincount++;
            Destroy(other.gameObject);
        }

    }
}


```
Score.cs
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class Score : MonoBehaviour
{
    // Start is called before the first frame update
    public int coincount;
    public Text value;
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        value.text = coincount.ToString();
        
    }
}

```

### Output:

<img width="1264" height="719" alt="Screenshot 2026-09-21 101439" src="https://github.com/user-attachments/assets/0da71ae0-8c50-40e3-8a31-ca2061433f2c" />

<img width="1265" height="695" alt="Screenshot 2026-09-21 101514" src="https://github.com/user-attachments/assets/f2b777a3-44a7-4e57-bb6a-aaa8a7db1501" />


### Result:
Thus the game was developed using Unity and adopted to AI technology.
