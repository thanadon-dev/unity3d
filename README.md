# unity3d
ฝึกสร้างเกมจ้า

# เดิน

```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class automove : MonoBehaviour
{
    public Transform Cameramove;
    public float Movespeed;

    void Start()
    {
        
    }
    void Update()
    {
        markControl();
    }
    //ควบคุมการเดินไปข้างหน้า
    public void cameramove()
    {
        transform.position += Cameramove.forward * Movespeed * Time.deltaTime;
    }

    //การควบคุมทิศทาง 
    public void markControl()
    {
        if (Input.GetKey("w"))
        {
            transform.position += Cameramove.forward * Movespeed * Time.deltaTime;
        }
        if (Input.GetKey("s"))
        {
            transform.position -= Cameramove.forward * Movespeed * Time.deltaTime;
        }
        if (Input.GetKey("d"))
        {
            transform.position += Cameramove.right * Movespeed * Time.deltaTime;
        }
        if (Input.GetKey("a"))
        {
            transform.position -= Cameramove.right * Movespeed * Time.deltaTime;
        }
    }

}



```

# กล้อง & หมุน
```
﻿using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Rotate : MonoBehaviour
{
    public Transform Movement;
    public Vector3 offset;
    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        controlRotate();
    }
    public void controlRotate()
    {
        transform.position = Movement.position + offset;
        if (Input.GetKey("q"))
        {
            transform.Rotate(Vector3.up * -90 * Time.deltaTime);
        }
        if (Input.GetKey("e"))
        {
            transform.Rotate(Vector3.up * 90 * Time.deltaTime);
        }
    }
}
```

# คะแนน
```
﻿using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;


public class score : MonoBehaviour
{
    public int score;
    public Text ScoreText;

    // Start is called before the first frame update
    void Start()
    {
        score = 0;
    }

    public void OnTriggerEnter(Collider other)
    {
        if(other.tag == "SCORE")
        {
            score++;
            Debug.Log(score);
            ScoreText.text = "SCORE = " + score;
            Destroy(other.gameObject);
        }
    }
}
```

# ศัครูเดินตาม
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class enimy : MonoBehaviour
{
    public Transform traget;
    public float Movespeed;
    public float weakup;
    // Start is called before the first frame update
    void Start()
    {

    }

    // Update is called once per frame
    void FixedUpdate()
    {
        transform.LookAt(traget);
        float dis = Vector3.Distance(traget.position, transform.position);
        if (dis < weakup)
        {
            transform.Translate(Vector3.forward * Movespeed * Time.deltaTime);
        }
    }
}
```
# ยิงปืน

```
﻿using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Gun : MonoBehaviour
{
    public GameObject bullet;
    public GameObject bulletPrefab;
    public Transform bulletSpawn;

    void Start()
    {
        
    }

    void Update()
    {
        Gunker();
    }

    public void Gunker()
    {
        if (Input.GetKey("h"))
        {
            bullet = (GameObject)Instantiate(bulletPrefab,
                new Vector3(bulletSpawn.position.x,
                bulletSpawn.position.y + 1.5f, 
                bulletSpawn.position.z),
                bulletSpawn.rotation);

            bullet.GetComponent<Rigidbody>().velocity = bullet.transform.forward * 10;
            Destroy(bullet, 2.0f);
            return;

        }
    }
}
```
