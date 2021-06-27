# n3st0r_role_entropy
Ansible role to configure entropy in system

## Check actual entropy
Entropy is the measure of the random numbers available from `/dev/urandom`:
```bash
cat /proc/sys/kernel/random/entropy_avail
```
If all’s well, it should be above 1000 but below the maximum value of 4096 bits.
If it is rather low (<1000), you should probably install haveged.
Otherwise cryptographic applications will block until there is enough entropy available

To watch entropy accumulation in real time, type:
```
watch -n 1 cat /proc/sys/kernel/random/entropy_avail
```

## Configure entropy level

```yaml
n3st0r_role_entropy_watermark: 2048
```
