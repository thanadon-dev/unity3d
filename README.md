# คำสั่ง Unity3d เบื้องต้นจ้า

* [(นับถอยหลัง)Countdown](#Countdown)

* [(ออก)Exit](#Exit)

* [(ปืน)Gun](#Gun)

* [(การเคลื่อนที่)Movement](#Movement)

* [(การหมุน)Rotate](#Rotate)

* [(ศัตรู)Running](#Running)

* [(เปลี่ยนหน้า)screen](#screen)

* [(การเก็บคะแนน)score](#score)


# Countdown
```c#
﻿using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class Countdown : MonoBehaviour
{
    public float Ctd = 5f;
    public Text textcountdown;
    public Canvas GAMEOVER;



    void Start()
    {

    }

    void Update()
    {

        if (Ctd > 0)
        {
            Ctd -= Time.deltaTime;
            textcountdown.text = "" + Ctd.ToString("###");
        }
        else
        {
            GAMEOVER.enabled = true;
        }
    }

}
```
# Exit
```c#
﻿using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.SceneManagement;


public class Exit : MonoBehaviour
{
    public void Exiting()
    {
        Debug.Log("Exit");
        Application.Quit();
    }
}
```
# Gun
```c#
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
# Movement
```c#
﻿using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Movement : MonoBehaviour
{
    public Transform Movement;
    public float Movespeed;
    // public Vector3 offset;

    void Start()
    {
        
    }

    void Update()
    {
        controlK();
       // controlRotate();
    }
    public void controlK()
    {
        if (Input.GetKey("w"))
        {
            transform.position += Movement.forward * Movespeed * Time.deltaTime;
        }

        if (Input.GetKey("s"))
        {
            transform.position -= Movement.forward * Movespeed * Time.deltaTime;
        }

        if (Input.GetKey("d"))
        {
            transform.position += Movement.right * Movespeed * Time.deltaTime;
        }

        if (Input.GetKey("a"))
        {
            transform.position -= Movement.right * Movespeed * Time.deltaTime;
        }

        if (Input.GetKey("t"))
        {
            transform.Rotate(Vector3.up * -90 * Time.deltaTime);
        }
        if (Input.GetKey("y"))
        {
            transform.Rotate(Vector3.up * 90 * Time.deltaTime);
        }
    }
}
```
# Rotate
```c#
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
# Running
```c#
﻿using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class runing : MonoBehaviour
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
        if(dis< weakup)
        {
            transform.Translate(Vector3.forward * Movespeed * Time.deltaTime);
        }
    }
}
```
# screen
```c#
﻿using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.SceneManagement;

public class Scane : MonoBehaviour
{
    public void PlayGeam()
    {
        SceneManager.LoadScene(SceneManager.GetActiveScene().buildIndex + 1);
    }
}
```
# score
```c#
﻿using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;


public class SCORE : MonoBehaviour
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
