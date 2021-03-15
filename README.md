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
