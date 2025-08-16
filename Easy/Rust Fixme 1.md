on fixing the syntax error of rust, you get the output:
`[112, 105, 99, 111, 67, 84, 70, 123, 52, 114, 51, 95, 121, 48, 117, 95, 52, 95, 114, 117, 36, 116, 52, 99, 51, 48, 110, 95, 110, 48, 119, 63, 125]`

Here's the original code:
``let hex_values = ["41", "30", "20", "63", "4a", "45", "54", "76", "01", "1c", "7e", "59", "63", "e1", "61", "25", "7f", >`
This sets the hexadecimal values(hex values for ascii of alphabets)

`    // Convert the hexadecimal strings to bytes and collect them into a vector
`    let encrypted_buffer: Vec<u8> = hex_values.iter()
``        .map(|&hex| u8::from_str_radix(hex, 16).unwrap())
 ``       .collect();`
Encrypts the hex list to byte (0-255 range) and collects them into a vector

    // Create decrpytion object
    let res = XORCryptor::new(&key);
    if res.is_err() {
        return; // How do we return in rust?
    }
    let xrc = res.unwrap();
Decryption object, sets the function for decrypting

    // Decrypt flag and print it out
    let decrypted_buffer = xrc.decrypt_vec(encrypted_buffer);
    println!("{:?}",decrypted_buffer);
'decrypted_buffer' is the xrc decryption of encrypted_buffer.
Order of conversions:
Hexadecimal -> (encrypt) bytes wrapped -> (decrypt) bytes unwrap -> print decrypted 
So decrypted is in bytes, which are just the ascii values of the letters

<h6>Convert manually online</h6>
![[Screenshot_2025-07-28_03_10_02.png]] 
<h5>OR:</h5>
<h6>Use code</h6>
`let decrypted_buffer = xrc.decrypt_vec(encrypted_buffer);
``    let text=String::from_utf8(decrypted_buffer).unwrap();
``    println!("{:?}",text);`

both give the output flag!