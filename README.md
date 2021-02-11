# unity3d
ฝึกสร้างเกมจ้า


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
