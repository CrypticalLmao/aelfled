# aelfled
//
//  appApp.swift
//  app
//
//  Created by Hany Mahrous on 3/9/23.
//

import SwiftUI

@main
struct appApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
import UIKit

class LoginViewController: UIViewController {
    
    // MARK: - Outlets
    
    @IBOutlet weak var usernameTextField: UITextField!
    @IBOutlet weak var passwordTextField: UITextField!
    
    // MARK: - View Lifecycle
    
    override func viewDidLoad() {
        super.viewDidLoad()
        setupUI()
    }
    
    // MARK: - Actions
    
    @IBAction func loginButtonTapped(_ sender: UIButton) {
        guard let username = usernameTextField.text, let password = passwordTextField.text else {
            return
        }
        
        if username == "cryptic" && password == "admin" {
            // Show home page
            let homeVC = HomeViewController()
            navigationController?.pushViewController(homeVC, animated: true)
        } else {
            // Show error message
            let alert = UIAlertController(title: "Invalid Credentials", message: "Please enter a valid username and password.", preferredStyle: .alert)
            alert.addAction(UIAlertAction(title: "OK", style: .default, handler: nil))
            present(alert, animated: true, completion: nil)
        }
    }
    
    // MARK: - Private Functions
    
    private func setupUI() {
        view.backgroundColor = UIColor.blue
        usernameTextField.placeholder = "Username"
        passwordTextField.placeholder = "Password"
    }
}

class HomeViewController: UIViewController {
    
    // MARK: - View Lifecycle
    
    override func viewDidLoad() {
        super.viewDidLoad()
        setupUI()
    }
    
    // MARK: - Actions
    
    @IBAction func logoutButtonTapped(_ sender: UIButton) {
        navigationController?.popViewController(animated: true)
    }
    
    // MARK: - Private Functions
    
    private func setupUI() {
        view.backgroundColor = UIColor.blue
        let homeButton = UIButton(frame: CGRect(x: 0, y: 0, width: 150, height: 50))
        homeButton.setTitle("Home", for: .normal)
        homeButton.addTarget(self, action: #selector(homeButtonTapped), for: .touchUpInside)
        view.addSubview(homeButton)
        
        // Center the button in the view
        homeButton.translatesAutoresizingMaskIntoConstraints = false
        homeButton.centerXAnchor.constraint(equalTo: view.centerXAnchor).isActive = true
        homeButton.centerYAnchor.constraint(equalTo: view.centerYAnchor).isActive = true
        
        // Add a purple border to the button
        homeButton.layer.borderWidth = 2.0
        homeButton.layer.borderColor = UIColor.purple.cgColor
    }
    
    @objc private func homeButtonTapped() {
        // Do something when the home button is tapped
    }
}

class PasswordCreationViewController: UIViewController {
    
    // MARK: - Outlets
    
    @IBOutlet weak var newUsernameTextField: UITextField!
    @IBOutlet weak var newPasswordTextField: UITextField!
    
    // MARK: - View Lifecycle
    
    override func viewDidLoad() {
        super.viewDidLoad()
        setupUI()
    }
    
    // MARK: - Actions
    
    @IBAction func createPasswordButtonTapped(_ sender: UIButton) {
        guard let username = newUsernameTextField.text,      = newPasswordTextField.text else {
            return
        }
        
        // Save username and password to database
    }
    
    // MARK: - Private Functions
    
    private func setupUI() {
        view.backgroundColor = UIColor.blue
        newUsernameTextField.placeholder = "New Username"
        newPasswordTextField.placeholder = "New Password"
    }
}


